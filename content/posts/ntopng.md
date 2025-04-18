---
title: "Install nTopNG on Linux"
date: 2025-04-12
draft: false
type: posts
categories:
  - monitoring
tags:
  - top, ntop, ntopng
summary: "Install nTopNG on debian based distros"
---

# nTopNG
Follow the provided commands to install ntopng on your system

## Ubuntu
```bash
apt-get install software-properties-common wget
add-apt-repository universe
wget https://packages.ntop.org/apt-stable/xx.yy/all/apt-ntop-stable.deb
apt install ./apt-ntop-stable.deb
```

## Debian
Before to install make sure to edit /etc/apt/sources.list and add "contrib" at the end of each line that begins with deb and deb-src.

``codename`` could be bullseye, bookworm or buster.
  
```bash
wget https://packages.ntop.org/apt-stable/<codename>/all/apt-ntop-stable.deb
apt install ./apt-ntop-stable.deb
```
  
## Installation
Note that ntopng must not be installed together with nedge. Remove ntopng before installing nedge.

nTopNG
```bash
apt-get clean all
apt-get update
apt-get install pfring-dkms ntopng pfring-drivers-zc-dkms
```
nEdge
```bash
apt-get install nedge
```

## Sample nTopNG Configuration
path is ``/etc/ntopng/ntopng.conf``
```config
#         The  configuration  file is similar to the command line, with the exception that an equal
#        sign '=' must be used between key and value. Example:  -i=p1p2  or  --interface=p1p2  For
#        options with no value (e.g. -v) the equal is also necessary. Example: "-v=" must be used.
#
#
#       -G|--pid-path
#        Specifies the path where the PID (process ID) is saved. This option is ignored when
#        ntopng is controlled with systemd (e.g., service ntopng start).
#
-G=/var/run/ntopng.pid
#
#       -e|--daemon
#        This  parameter  causes ntop to become a daemon, i.e. a task which runs in the background
#        without connection to a specific terminal. To use ntop other than as a casual  monitoring
#        tool, you probably will want to use this option. This option is ignored when ntopng is
#        controlled with systemd (e.g., service ntopng start)
#
# -e=
#
#       -i|--interface
#        Specifies  the  network  interface or collector endpoint to be used by ntopng for network
#        monitoring. On Unix you can specify both the interface name  (e.g.  lo)  or  the  numeric
#        interface id as shown by ntopng -h. On Windows you must use the interface number instead.
#        Note that you can specify -i multiple times in order to instruct ntopng to create  multi-
#        ple interfaces.
#
# -i=eth1
# -i=eth2
#
#       -w|--http-port
#        Sets the HTTP port of the embedded web server.
#
-w=3002
#
#       -m|--local-networks
#        ntopng determines the ip addresses and netmasks for each active interface. Any traffic on
#        those  networks  is considered local. This parameter allows the user to define additional
#        networks and subnetworks whose traffic is also considered local in  ntopng  reports.  All
#        other hosts are considered remote. If not specified the default is set to 192.168.1.0/24.
#
#        Commas  separate  multiple  network  values.  Both netmask and CIDR notation may be used,
#        even mixed together, for instance "131.114.21.0/24,10.0.0.0/255.0.0.0".
#
# -m=10.10.123.0/24,10.10.124.0/24
#
#       -n|--dns-mode
#        Sets the DNS address resolution mode: 0 - Decode DNS responses  and  resolve  only  local
#        (-m)  numeric  IPs  1  -  Decode DNS responses and resolve all numeric IPs 2 - Decode DNS
#        responses and don't resolve numeric IPs 3 - Don't decode DNS responses and don't  resolve
#
# -n=1
#
#       -S|--sticky-hosts
#        ntopng  periodically purges idle hosts. With this option you can modify this behaviour by
#        telling ntopng not to purge the hosts specified by -S. This parameter requires  an  argu-
#        ment  that  can  be  "all"  (Keep  all hosts in memory), "local" (Keep only local hosts),
#        "remote" (Keep only remote hosts), "none" (Flush hosts when idle).
#
# -S=
#
#       -d|--data-dir
#        Specifies the data directory (it must be writable by the user that is executing ntopng).
#
# -d=/var/lib/ntopng
#
#       -q|--disable-autologout
#        Disable web interface logout for inactivity.
#
# -q=
#
# Define nDPI custom protocols
#
#--ndpi-protocols=/etc/ntopng/custom_protocols.txt
# Use prefix due to nginx proxy
#--http-prefix="/ntopng"

# Everybody's admin
#--disable-login=1

# Do not resolve any names
--dns-mode=3

# Limit memory usage
--max-num-flows=10000
--max-num-hosts=10000
--community
```

### ARM64 Images
```
sudo docker run --privileged --restart=always -d -p 3002:3000 --net=host ntop/ntopng_arm64.dev:latest -i eth0
```