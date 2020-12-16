---
title: "GSoC 2018 – Community Bonding Part 3: Management of LVM VGs in Calamares"
date: "2018-05-12"
coverImage: "7782091.png"
---

Hello!

I talked in my last [post](https://caiojcarvalho.wordpress.com/2018/05/11/google-summer-of-code-2018-community-bonding-part-2-studies-about-lvm/) about some of my LVM studies for the first goal of GSoC. This post is an addition to the last one, focused more in explaining how I want to implement it and talking a little bit about some application concepts from Calamares that I've studied.

## LVM VGs in Calamares

### Operation Management with JobQueue

KDE Partition Manager uses a stack of pending operations as a way to manage and execute processes in volumes. As I've said in my previous post, Calamares doesn't work in this way and uses a global JobQueue instance that collects pending Jobs and execute all of them when the GUI reaches the last view step (i.e. ExecutionViewStep).

These Jobs are collected according to its origin modules. Calamares is an application which can use multiple plugin modules (and you can identify them at GUI as the option chooser interfaces, e.g. keyboard, partition, users). You can see a brief description of Calamares structure [here](https://github.com/calamares/calamares/wiki/Design-Notes).

### Jobs in Partition module

At Partition module, the Jobs are managed by the PartitionCoreModule instance, which represents this module. Each available device is associated to a collection of Jobs (e.g. create partition, delete partition, resize partition) and the module collects these Jobs based on it.

### Volume Groups Jobs and GUIs

So it will be necessary to create a dialog that will communicate with a button available at the Partition page (as I said in my previous post as well). After this dialog is opened and the options for the newly VG are confirmed, this information will be passed to a method called PartitionCoreModule::createVolumeGroup() that I'll implement, which will create an instance of CreateVolumeGroupJob with the necessary data for the new VG and will load the new LVM device at the storage device combobox, allowing the user to choose it and manipulate its logical volumes. When executed, CreateVolumeGroupJob will use a CreateVolumeGroupOperation (from kpmcore) to create the new VG.

And about the other VG manipulations (i.e. resize and delete), I'm planning to create a widget hierarchy to reuse  in the resize view, which will include some concepts from the VG creation interface. It will be similar to how its implemented in KPM. And before deleting a LVM device, it will be needed to deactivate it, where I think that just including another button or action to do this operation is ok, and  remove it from the device list combobox afterwards.

## Conclusion

There are more details in this implementation, but I decided to create a brief description of the most important in this post, just to organize my ideas. I'll start implementing it during this Monday. This first goal will be fine to complete.

Until the next post! :)
