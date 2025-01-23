---
layout: post
title:  "Data Processing Libraries and Frameworks - The Environment"
date:   2025-01-23 22:52:10 +0200
categories: data processing engineering hardware
---
## So many data processing frameworks and libraries

## Introduction

A few high cloud bills ago, I decided to have another look at a homelab.  Having abandonned it at the time for reasons of maintenance and running cost, I decided to consolidate my running services on a few Raspberry Pis and use the cloud providers like GCP and AWS for my workload experimentation.  Since a while, there has been a huge price drop of the Intel Haswell (E5 2600 v3) and Broadwell (E5 2600 v4) microarchitectures.  Even gamers have picked those up in both single and dual socket layouts as budget friendly gaming rigs.  To me, that sounds a bit enthousiastic, since gaming prefers better single core performance over multi core performance.  However, these processors have decent L3 cache, so maybe that has something to do with it.  Anyway, data processing using frameworks like spark and ML workloads definitely prefer multi core with loads or memory.

I was able to source a pretty decent used starting platform online for cheap, consisting of a 2 socket motherboard, with 2 E5 2620 v4 CPUs, 128GB of DDR4 2333MHz memory, nicely spread over the available memory lanes.  It came in a nice case with 1000W PSU.  No GPU apart from the Aspeed onboard graphics, and no disks.  No problem.  Found a few refurbished E5 2699 v3 (18cores/36threads each), paired that with an RTX 2060 nvidia GPU, a PCIe x16 NVMe interface, a 2T WD NVMe drive, 6 2TB WD HDD spindles (RAID10), an additional 4TB WD HDD (red) and a few SATA ssd drives as well.  The Asus z10pe-d16 motherboard has plenty of interface options, including an onboard RAID controller.

Something that surprised me, is how many people try to sell their not-so-well working computers and parts as fully operational and in "as good as new" state.  

## The Problems

### PC
The motherboard was not entirely connected to the case. Apart from power and only a couple of fans, nothing was connected.  When I went to pick up the thing, the seller assured me that he just tested everything and it all worked fine.  OMG no.  I started connecting everything (fans, power and reset switches), installed a tiny GPU I had laying around, and the system booted.  Installed Debian12 on a temp sata ssd, to have a look and run some stress tests.  Ok, both cpus and memory were detected.  OS installation went fairly smooth.  So, I went ahead and ordered the PCIe NVMe interface, the NVMe drive and an exhaust fan for the back of the case.  I also had a set of E5 2699 v3 cpus coming in the mail.  These were really cheap compared to the v4 versions, but couldn't justify the price difference.  This was going to stay within budget.

When all that arrived, I started installing the components.  The PCIe NVMe adapter supports 4 drives, but only when your motherboard and BIOS support bifurcation.  Mine doesn't out of the box, but I did read up on this on the internet, and found that a few were able to modify the BIOS to unlock this feature.  As I only have 1 drive now, I parked that for later.  

The RTX 2060 GPU needs an additional power connection, and using the cable that was already there, the PC did not boot and immediately shut down.
After some investigation, seems the cable is broken causing a short circuit. Later, I had the same problem with a sata power cable which ruined a drive.  

The RTX 2060 was pulled from my son's computer, which I replaced with a used RTX 2080 Super.  The guy selling the 2080 guaranteed it worked fine and he just replaced it with the 4090.  Running the FurMark GPU stress test on the 2080, revealed serious temperature throttling.  At the slightest graphics processing, the fans would aggressively spin up to 100%.  Where I was getting 100fps using the same test on the 2060, I expected about 50% better performance of the 2080.  NVIDIA Inspector immediately showed the thermal throttling.  Fortunately, these cards are easy to maintain and cleaning up the dry power residue and replacing it with fresh thermal paste on the GPU was a quick but effective fix.  Went from 40fps with noisy fans to almost silent 170fps.  




