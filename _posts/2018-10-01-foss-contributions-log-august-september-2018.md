---
title: "FOSS Contributions Log - Aug/Sept 2018"
date: "2018-10-01"
---

Hi!

I am starting a new type of post in my blog, which I will be using as a type of monthly report/log to track my free software contributions. :)

This post will be related not only to the last month (September), but I have decided to include my experiences from August as well. In the last month, I was very occupied with some assignments from the university after the two week travel that I had in August for [Akademy](https://carvalho.site/2018/08/18/akademy-2018-was-great/) and [ERBASE](http://erbase.sbc.org.br/2018/wticgbase.html) (which is a congress that I had presented a paper). I am in the end of this semester in the university, so I am anxious for my vacations to code more in the projects that I contribute to.

Well, following this brief comment about Akademy, I will start talking about what I have done in KDE in the weeks of August/September. I am still working in that RAID patch on KDE Partition Manager, where I still got some problems with device mapping and udev. The RAID arrays are not been mapped as I expected. Also there are some bugs related to partition creation inside of RAID and another one related to udev, that is keeping the device busy, which will raise some errors when you try to do any disk operation.

Besides that, I am aiming to fix these problems soon and make RAID great in kpmcore. Here is a list with some important patches that I have done to kpmcore meanwhile (as you can see in [raid-support branch](https://cgit.kde.org/kpmcore.git/?h=raid-support)):

- Changed CreateVolumeGroupJob to support RAID, finally allowing RAID creation.
- Implemented RAID deactivation.
- Support for configuration of custom mdadm.conf paths in KDE Partition Manager.
- mdadm.conf is being updated after RAID creation through an application helper (for compatibility with the KAuth DBus service whitelist in kpmcore).
- Improved the layout of Volume Group GUI in KDE Partition Manager.
- Allowed RAID creation only with LinuxRaidMember, Unformatted or Unknown, to avoid deleting important partitions.

I am trying to finish RAID activation, there is just some work to do in kpmcore to finish it. I had implemented the GUI action in KDE Partition Manager, but I couldn't finish the implementation of the Operations and Jobs in the library. Hope to get some time in October to contribute more and to finish these pending parts. Remembering that [LaKademy 2018](https://br.kde.org/node/15901) is near and I will be participating there. And I got the opportunity to contribute to KDE as a [Google Code-in 2018](https://codein.withgoogle.com/) mentor! YAY! :)

And about my contributions to other FOSS projects out of KDE umbrella...

I am starting communicating to [mlpack library](https://github.com/mlpack/mlpack) community to contribute there as well. I am a machine learning enthusiast and beginner researcher of this area, so I started studying about this library and I was thinking about contributing to this [feature request](https://github.com/mlpack/mlpack/issues/1254), which will provide a simple CLI application to access mlpack's artificial neural networks module. Actually I am just trying to understand its codebase as I have no previous experience with C++ template metaprogramming and this library is built using this paradigm. Such a nice opportunity to learn new things and a great challenge! Hope to write more news about my progress on it. :)
