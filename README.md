# Linux-Storage-Management-Project-Part-2
# Linux Storage Management Part 2 (Formatting, Mounting, Persistent Filesystems, and LVM Expansion)

<img width="787" height="546" alt="Linux Storage Management - Part 2 pic 29" src="https://github.com/user-attachments/assets/321fcaeb-b5ce-498b-a809-44e6f2c846bf" />

## 📝 Overview

## This project builds on **Part 1 (Linux Disk Partitioning — Creating 6 Partitions on a 20GB Disk)** and focuses on turning raw partitions into usable, managed storage. In this phase, I:

#### - Formatted new partitions with ext4
#### - Created and mounted filesystem mount points
#### - Configured **persistent mounts** using /etc/fstab
#### - Prepared selected partitions for **LVM**
#### - Created and extended a **volume group (VG)**
#### - Created and extended a **logical volume (LV)**
#### - Resized the filesystem to consume the extended space

#### This work simulates real‑world Linux system administration tasks around storage provisioning, filesystem management, and logical volume expansion.

## 🖥️ Environment:

#### - OS: CentOS 9 Stream (VirtualBox VM)

#### - Disk: /dev/sdb - 20 GB virtual disk (from Part 1)

#### - Tools Used: lsblk, mkfs.ext4, mount, /etc/fstab, pvcreate, vgcreate, vgextend, lvcreate, lvextend, pvs, vgs, lvs

#### - Volume Group: vg_data

#### - Logical Volume: lv_data 

# 🚀 Project Steps

## Verify Existing Partitions

I started from the partition layout created in Part 1. Verifying existing partitions

Using the "lsblk" command

This confirmed:
- /dev/sdb1, /dev/sdb2, /dev/sdb3 → primary partitions
- /dev/sdb4 → extended partition
- /dev/sdb5, /dev/sdb6 → logical partitions inside the extended partition

<img width="617" height="302" alt="Linux Storage Management - Part 2 pic 1" src="https://github.com/user-attachments/assets/bcb3259a-94f5-4da7-8632-9ca0821cfc8a" />

## Format Partitions with ext4, I chose /dev/sdb1 and /dev/sdb2 to act as standard filesystems. 

<img width="693" height="386" alt="Linux Storage Management - Part 2 pic 2" src="https://github.com/user-attachments/assets/154513bc-9942-44ff-9ab1-a96a3915fff6" />

## Create Mount Points for the File System Filesystems

<img width="690" height="277" alt="Linux Storage Management - Part 2 pic 3" src="https://github.com/user-attachments/assets/92859870-2486-4163-bb01-665a77d736f5" />

## Configure Persistent Mounts with /etc/fstab
Ensure the filesystems mount automatically at boot

<img width="692" height="371" alt="Linux Storage Management - Part 2 pic 4" src="https://github.com/user-attachments/assets/8d47c65f-834d-4650-91e3-b5dc0bbadf09" />

<img width="671" height="777" alt="Linux Storage Management - Part 2 pic 5" src="https://github.com/user-attachments/assets/8262e4d0-dc03-4a30-bd75-2a618b69826c" />

<img width="558" height="103" alt="Linux Storage Management - Part 2 pic 6" src="https://github.com/user-attachments/assets/b466bddb-fc43-4cb8-891f-786b497756bd" />

<img width="920" height="385" alt="Linux Storage Management - Part 2 pic 7" src="https://github.com/user-attachments/assets/d1b10b27-294a-4537-b0bb-e1fae915e061" />

