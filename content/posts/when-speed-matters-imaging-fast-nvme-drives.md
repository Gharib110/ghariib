---
title: "When Speed Matters: Imaging Fast NVMe Drives"
date: 2025-01-15
tags: 
  - "6g"
  - "ces"
  - "disk-imaging"
  - "ssd"
---

![](https://blog.elcomsoft.com/wp-content/uploads/2024/10/nvme-speed.jpg)

Modern NVMe SSDs require specialized approaches for forensic analysis. Each year, the speed and capacity of these devices grow, presenting significant challenges related to both the speed and reliability of transferring large volumes of data when capturing disk images. In this article, we will test the imaging of a high-speed Samsung 980Pro NVMe drive with OSForensics and FTK Imager. As a bonus, we also tested a prototype of our NVMe write-blocker, which yielded some intriguing results.

## **The Issue of Fast Storage Devices**

At first glance, imaging a high-speed SSD seems a lot faster than dealing with a slower one. However, fast storage devices introduce a range of issues that are not typically encountered with slower SATA drives. Here are just a few:

1. **USB bandwidth limitations**: When performing a forensic extraction, one cannot just connect the NVMe device to the computer’s M.2 slot. Instead, one has to use a write-blocking adapter, which are typically connected to a USB port. In turn, this means that peak read speeds of a fast SSD are never reached even if connected to a fast 10gbps USB 3.2 Gen 2 port. Using a faster Gen 2×2 or USB4 port is not always a perfect solution, because…
2. **10gbps adapters for connecting NVMe drives to USB**: These common adapters typically work at a small fraction of the speed advertised by even the slowest NVMe drives. Faster adapters require higher-speed USB ports, which aren’t always accessible, but there aren’t many write-blocking adapters that cross the 10gbps barrier.
3. **USB adapters tend to overheat**: This is especially true when drives are connected temporarily without proper cooling. The lack of adequate cooling, like single-use silicone thermal pads and metal heat sinks, leads to thermal throttling, which causes a sharp drop in performance.
4. **Quality hardware required for stable extraction**: The quality and performance of the USB port, cable, and adapter all influence overall stability. We’ve also encountered severe slowdowns when the computer was running on battery power as opposed to plugged-in.
5. **Sustained write speed of the target drive matters**: Even if everything else is perfect, the imaging speed is affected by the _sustained write speed_ characteristic of the target drive. Do not confuse this with _peak continuous write speed_ that gets listed in manufacturer specs, as the _sustained_ speed is significantly lower and tends to decrease sharply based on the volume of data being written and the remaining free space on the target drive.

In real-world scenarios, achieving imaging speeds that come close to the advertised _continuous read speed_ of the SSD drive is nearly impossible. The adjusted goal is much more modest; we are aiming at the bandwidth of the “USB port + adapter” combination, which is generally around 10 gigabits per second. Considering USB overhead, the theoretical maximum speed is roughly 1 GB/s.

## From SATA to NVMe

We’ve previously published detailed benchmarks based on imaging some SATA drives. In Maximizing Disk Imaging Speeds and When Speed Matters: Optimizing Disk Imaging, we discussed the various implications of disk imaging with different forensic tools. Those two articles, however, were dealing with SATA drives, which are much slower compared to modern NVMe devices. This time, we focused on NVMe drives rather than SATA ones. Although we ran a preliminary check with SATA drives to confirm the setup, as expected, the results mirrored our previous tests. The drive we used for the main tests was a Samsung 980Pro NVMe SSD (256 GB).

## **Test Environment and Setup**

For this round of testing, we used a different laptop – specifically, a Tecno MEGABOOK S1, featuring an Intel Core i7-13700H processor, 32 GB of RAM, and a fast 1 TB PCIe Gen4x4 SSD. The laptop includes USB 3.2 Gen2 and USB 4 ports.

The NVMe drive we imaged (the 256GB Samsung 980 Pro) was connected to a 10-gigabit Type-C port via a dedicated NVMe to USB adapter, while the image was saved to the laptop’s internal NVMe SSD. This setup ensures a significant speed margin for handling large volumes of data.

We performed data copying tests with both external power and battery power. Unlike previously found on a differenc system, this particular laptop did not demonstrate any speed reduction when switching to battery power. The reason for this discrepancy remains unclear.

The tools we used, in their latest versions, are familiar: OSForensics and FTK Imager.

## **Test Results**

As expected, OSForensics again delivered the best performance. When we connected the NVMe drive to a USB 4.0 port, the average imaging speed exceeded 1 GB/s (specifically, it reached 1007 MB/s), and the image was completed in just 4 minutes. When the same drive was connected to a USB 3.2 Gen 2 port, the speed dropped by about 1%, indicating that the limiting factor wasn’t the USB port but the adapter used to connect the drive.

In comparison, FTK Imager was considerably slower, taking 7.5 minutes to complete the same task, with an average speed of 525 MB/s, nearly half the rate achieved by OSForensics.

Finally, we tested the performance of our prototype NVMe write-blocker. The results exceeded even our expectations: with full write protection enabled, the copying speed reached 965 MB/s, just 4% slower than when using a standard NVMe adapter without protection.

## **What’s Next?**

SATA and NVMe storage devices are the most common types of storage media, apart from USB drives, flash drives, and memory cards used in cameras, dashcams, and smartphones. We plan to address these other storage media soon. Additionally, we are eager to test software-based write blockers, standalone blockers, and to run similar tests in Lunix.

## **Conclusion**

We’ve already discussed the importance of maximizing speeds during forensic analysis; any time saved is truly invaluable. However, achieving high imaging speeds requires the right combination of everything: computers, cables, adapters, write blockers, and even the target storage device all affect the imaging speed.

Go to Source
