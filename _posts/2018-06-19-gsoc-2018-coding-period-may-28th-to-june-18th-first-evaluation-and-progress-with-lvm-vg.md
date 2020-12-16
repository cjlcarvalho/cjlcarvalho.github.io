---
title: "GSoC 2018 – Coding Period (May 28th to June 18th): First Evaluation and Progress with LVM VG"
date: "2018-06-19"
coverImage: "gsoc-vertical-wide-gray-text-white-bg.png"
---

Hi!

The first evaluation was done and I successfully passed! 🙂

I got some problems during the last weeks of Google Summer of Code which made me deal with some challenges. One of these challenges was caused by a HD physical problem. I haven’t made a backup of some work and had to rework again in some parts of my code. As I already knew how to proceed, it was faster than the first time.

I had to understand how the device loading process is made in Calamares to load a preview of the new LVM VG during its creation in Partition Page. I need to list it as a new storage device in this page and deal with the revert process. I’ve implemented some basic fixes and tried to improve it.

There were some problems when reverting pending operations, especially when you got an old LVM VG configured in your system. This problem was related to kpmcore scanDevice procedure. SfdiskBackend::scanDevice method is responsible to load a device based on its partition node, but it only was considering disk devices and ignoring logical devices.

LVM VGs were only loaded using SfdiskBackend::scanDevices method, which loads all the devices found in your system. Calamares uses scanDevice during revert process, to update the devices references according with the original ones. So, when some old VG was previously configured, the revert process tries to call scanDevice and was getting only a nullptr reference, causing an unexpected segfault.

I fixed this method to load the specified VG, but my solution needs to know all the physical devices contained in your system to do it, as you can see in this commit:

[https://cgit.kde.org/kpmcore.git/commit/?id=358957641b2c7ff6b69d090c9e1fddba482c6817](https://cgit.kde.org/kpmcore.git/commit/?id=358957641b2c7ff6b69d090c9e1fddba482c6817)

As you can imagine, it can take a significant time of processing in some cases, because it will load all the devices every time when you need to load a specific VG. I need to improve it, using some other procedure, but I’m worried about the loading of LVM PVs, that will require to load each device which the PV is associated.

About my progress in Calamares during this time, you can take a look in some commits in my PR:

[https://github.com/calamares/calamares/pull/984](https://github.com/calamares/calamares/pull/984)

Well, it’s being a great experience, but I need to improve some things in my work and in its processes, especially with the communication, I’m learning about how to be a more communicative person in open source projects. I'm getting a great knowledge! 🙂
