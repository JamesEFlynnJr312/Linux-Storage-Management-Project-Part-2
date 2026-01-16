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

### I started from the partition layout created in Part 1. Verifying existing partitions

### Using the "lsblk" command

### This confirmed:
- /dev/sdb1, /dev/sdb2, /dev/sdb3 → primary partitions
- /dev/sdb4 → extended partition
- /dev/sdb5, /dev/sdb6 → logical partitions inside the extended partition

<img width="617" height="302" alt="Linux Storage Management - Part 2 pic 1" src="https://github.com/user-attachments/assets/bcb3259a-94f5-4da7-8632-9ca0821cfc8a" />

## Format Partitions with ext4, I chose /dev/sdb1 and /dev/sdb2 to act as standard filesystems. 

<img width="693" height="386" alt="Linux Storage Management - Part 2 pic 2" src="https://github.com/user-attachments/assets/154513bc-9942-44ff-9ab1-a96a3915fff6" />

## Create Mount Points for the File System Filesystems

<img width="690" height="277" alt="Linux Storage Management - Part 2 pic 3" src="https://github.com/user-attachments/assets/92859870-2486-4163-bb01-665a77d736f5" />

## Configure Persistent Mounts with /etc/fstab
### Ensure the filesystems mount automatically at boot

<img width="692" height="371" alt="Linux Storage Management - Part 2 pic 4" src="https://github.com/user-attachments/assets/8d47c65f-834d-4650-91e3-b5dc0bbadf09" />

<img width="671" height="777" alt="Linux Storage Management - Part 2 pic 5" src="https://github.com/user-attachments/assets/8262e4d0-dc03-4a30-bd75-2a618b69826c" />

<img width="558" height="103" alt="Linux Storage Management - Part 2 pic 6" src="https://github.com/user-attachments/assets/b466bddb-fc43-4cb8-891f-786b497756bd" />

<img width="920" height="385" alt="Linux Storage Management - Part 2 pic 7" src="https://github.com/user-attachments/assets/d1b10b27-294a-4537-b0bb-e1fae915e061" />

## LVM Configuration and Expansion
### Prepare Partitions for LVM
### I selected /dev/sdb3, /dev/sdb5, and /dev/sdb6 as LVM physical volumes

<img width="692" height="397" alt="Linux Storage Management - Part 2 pic 8" src="https://github.com/user-attachments/assets/8618dedb-7083-4efd-b735-2d3f13f19256" />

<img width="693" height="692" alt="Linux Storage Management - Part 2 pic 9" src="https://github.com/user-attachments/assets/71c7bae9-6b37-4d0f-9e0e-c0f0ab832429" />

## Create the Volume Group (VG)
### I created a volume group named vg_data using /dev/sdb3:

<img width="692" height="196" alt="Linux Storage Management - Part 2 pic 10" src="https://github.com/user-attachments/assets/9487504c-fe60-4eb2-8404-9de134b0c014" />

### Verification of the Volume Group:

<img width="691" height="751" alt="Linux Storage Management - Part 2 pic 11" src="https://github.com/user-attachments/assets/ef73c877-c016-42e8-aad5-5d73758b9e0b" />

## Extend the Volume Group with vgextend
### To increase capacity, I added /dev/sdb5 and /dev/sdb6 to vg_data:

<img width="688" height="652" alt="Linux Storage Management - Part 2 pic 12" src="https://github.com/user-attachments/assets/68015bb0-bb1f-44df-aae9-35d24533c47e" />

## Create a Logical Volume (LV)
### I created a logical volume named lv_data using 2G of space from vg_data:

<img width="691" height="250" alt="Linux Storage Management - Part 2 pic 13" src="https://github.com/user-attachments/assets/1314f00c-2be0-4639-9071-e4dc0e4ef321" />

<img width="690" height="588" alt="Linux Storage Management - Part 2 pic 14" src="https://github.com/user-attachments/assets/48d71afe-9255-4ea5-986d-442009eaa2c0" />

## Format and create a mounting point for Logical Volume lv_data
### I formatted the LV with ext4:

<img width="693" height="402" alt="Linux Storage Management - Part 2 pic 15" src="https://github.com/user-attachments/assets/30d2031a-ee6d-4ce6-93a8-8e0613de0fb7" />

## Persistent Mount for the Logical Volume
### I added the LV entry into the /etc/fstab configuration file for a persistent mount:

<img width="690" height="157" alt="Linux Storage Management - Part 2 pic 16" src="https://github.com/user-attachments/assets/d99a382e-02fa-43af-94b9-86abf7993a96" />

<img width="695" height="643" alt="Linux Storage Management - Part 2 pic 17" src="https://github.com/user-attachments/assets/1eda2a5a-e8a5-4a82-a125-a479030851a3" />

<img width="696" height="451" alt="Linux Storage Management - Part 2 pic 18" src="https://github.com/user-attachments/assets/a2bb3678-20a8-43fa-9211-7567846c92c4" />

## Extending the Logical Volume and Filesystem
### I extended lv_data by 2G:

<img width="692" height="242" alt="Linux Storage Management - Part 2 pic 19" src="https://github.com/user-attachments/assets/fe1a0eb9-0bf4-4704-bf2c-42518013fc5e" />

<img width="737" height="823" alt="Linux Storage Management - Part 2 pic 20" src="https://github.com/user-attachments/assets/41e02986-302a-4388-9af1-710231ed9eb5" />

## 📘 Key Concepts Reinforced
#### - Filesystem creation: Using mkfs.ext4 to format partitions and logical volumes.
#### - Mounting and persistence: Using mount, df -hT, and /etc/fstab to manage and persist filesystems across reboots.
#### - LVM building blocks:
#### - pvcreate → physical volumes
#### - vgcreate / vgextend → volume groups
#### - lvcreate / lvextend → logical volumes
#### - Online growth: Extending logical volumes and resizing filesystems without recreating them.
#### - Separation of concerns: Using partitions as building blocks for both traditional filesystems and flexible LVM storage

## 🎯 What I Learned
#### - How to turn raw partitions into usable filesystems with ext4
#### - How to design and configure persistent mount points using /etc/fstab
#### - How to build and extend LVM volume groups and logical volumes
#### - How to safely grow storage capacity without data loss
#### - How these skills map directly to real‑world Linux, DevOps, and infrastructure roles



