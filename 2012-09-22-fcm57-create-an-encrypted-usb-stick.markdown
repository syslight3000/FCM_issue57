---
layout: post
title: "57期 - Create an Encrypted USB Stick"
date: 2012-09-22 13:35
comments: true
categories: HOW-TO
---

Written by Kalven Slade

Many articles seem to focus on using various utilities such as UNetbootin or Universal USB Installer from pendrivelinux.com, but none of these are necessary to install Ubuntu on a USB hard disk or flash drive, and they don't account for the possibility of losing your portable OS, which may contain personal information.

This guide will walk you through how to create an encrypted portable OS that will allow you to have a secure device where you can update and store files.

Everything in the document assumes that you are doing a fresh install of Ubuntu 10.04.2 (11.10 has also been tested to work,) and doing each step in order. This guide will also be easier to follow if you disconnect any other drives including internal ones except the CD/DVD. (If your other drive remains, make sure you place Grub on the correct disk!)

With this being a portable OS, using Xubuntu will make it faster on flash drives, and allows it to function on computers with lower memory requirements than Ubuntu.

Encryption will help you secure your data if you lose or have your computer stolen.

Ubuntu has built in support for two types of encryption by default, using the Alternate Install CD: full disk encryption, and profile/home encryption. You can add additional encryption using TrueCrypt.

A USB flash can be slow (sometimes too slow!); a USB or ESATA hard drive will function much better.

Linux, unlike Windows, can easily be moved from computer to computer, and boot from your portable drive.

Try to stay away from restricted features like 3d video support on your portable install.

Boot the Alternate Install CD for Ubuntu or Xubuntu, and choose install from the menu.

Unless you need to modify settings, just choose the defaults for your language, location, keyboard configuration, host name, and time zone.

Setting up your partitions is very important, and probably the hardest part to do correctly. You want to limit how often the drive is both read and written to; encryption adds a bit of overhead. EXT3 and EXT4 are too slow, also having a swap space will cause speed issues as well. I have found that it is best to create a FAT32 Partition for sharing files between Windows computers, and using EXT2 for your Ubuntu install.

Choose manual from the partition menu. Choose your USB drive (and not any existing partitions), and press Enter. It will ask you if you want to create an empty partition table on this device. Choose yes.

Below your drive, it should now be listed as free space. Choose it and create a new partition. This new partition will be your FAT32 partition for Windows transfers. I have a 16 GB flash drive, and choose to allocate 3 GB for my FAT32 partition. Make it a Primary partition, at the beginning of the disk. Change the file type to FAT32, and mount point to none. Then choose done setting up this partition.

Now we can create the Boot partition, choose your free space again, and create a new partition, 256 MB is good. Make sure you change from GB (Gigabytes) to MB (Megabytes), or you may not have enough space for your OS. Make it a Primary Partition at the beginning of the disk. Change the File system to EXT2, mount point to /boot, and bootable flags to on. Now you can choose done setting up this partition.

From the remaining free space, create a new primary partition with Physical volume for encryption as the file type, then choose done setting up this partition.

Choose Configure encrypted volumes from the menu, yes to write changes to the disk. Choose Create encrypted volumes, choose finish.

Create a password and verify.

You will now be back to the partitioner, and you will see a new encrypted volume drive is listed, select the partition (it will will have a file system of EXT4), and press enter.

Change the file system to EXT2, mount point to `/`, and choose done setting up partition.

Choose finish partitioning and write changes to disk.

Choose no when you see the warning about a missing mount point for the FAT32 partition and the missing SWAP partition, then yes to write changes to the disk.

Continue with the install, do not choose home directory encryption for flash drive installs.

Once installed, run updates, and reboot, then you’re done!

## Encryption Info

You can change and add passwords for your full disk encryption - 8 passwords are allowed, and they are numbered 0-7.

To see which keys are in use:

    sudo cryptsetup luksDump /dev/<drive>

Changing Your Password

To change your password you will need to first add a new one, and then remove the old one.

Step 1: Add New Password:

    sudo cryptsetup luksAddKey /dev/<drive>

Enter any passphrase: <your current password>

Enter new passphrase for key slot: 

Verify passphrase: 

Step 2: Remove Old Password:

run a dump again to verify key slot added:

    sudo cryptsetup luksDump /dev/<drive>

    sudo cryptsetup luksKillSlot /dev/<drive> <key slot number>

Enter any remaining LUKS passphrase: 

Verify removal with another dump:

    sudo cryptsetup luksDump /dev/<drive>
