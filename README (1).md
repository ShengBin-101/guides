---
description: >-
  In this guide, we are going to dual boot Ubuntu 22.04 LTS alongside Windows
  11.
cover: .gitbook/assets/ubuntu-22-04-jammy-jellyfish-wallpaper-800x450.jpg
coverY: 0
layout:
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 💻 Ubuntu Setup - Dual Booting (For Windows)

## **Pre-requisites**

* Windows 11 or Windows 10 running on your PC or Laptop
* 8GB or higher pen/thumb drive to create a bootable disk with Ubuntu Linux
* Reserve free space of at least 50GB on your drive.

## **Step 1: Download Ubuntu 22.04 LTS**&#x20;

Link to Download Page: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

<figure><img src=".gitbook/assets/image (7).png" alt="" width="375"><figcaption><p>Download Page (Ubuntu)</p></figcaption></figure>

## Step 2: Download Balena Etcher

This will be used to flash the iso image downloaded from Step 1 onto our USB drive.

Instead of Balena Etcher, you may use Rufus as an alternative. \
In this guide, we will use Balena Etcher.

Link to Download Page: [https://etcher.balena.io/](https://etcher.balena.io/)

<figure><img src=".gitbook/assets/image (1) (1).png" alt="" width="375"><figcaption><p>Download Page (Balena Etcher) - Part 1</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (2) (1).png" alt="" width="375"><figcaption><p>Download Page (Balena Etcher) - Part 2</p></figcaption></figure>

Once successfully downloaded and installed, you should see this window after launching Balena Etcher.

<figure><img src=".gitbook/assets/image (3) (1).png" alt="" width="375"><figcaption><p>Balena Etcher Interface</p></figcaption></figure>

## Step 3: Partition Disk Space for Ubuntu

Press the windows key and type in "disk management", select "open" for <mark style="color:purple;">"Create and format hard disk partitions"</mark>.

<figure><img src=".gitbook/assets/image (4) (1).png" alt="" width="375"><figcaption><p>Search for Disk Management on Windows</p></figcaption></figure>

In Disk Management, right click on the partition that you want to split. \
<mark style="color:blue;">**For me, I right click on C drive and select "Shrink Volume" to shrink a volume of 60GB.**</mark>

<figure><img src=".gitbook/assets/image (5) (1).png" alt="" width="375"><figcaption><p>How to Shrink Volume</p></figcaption></figure>

After specifying to shrink 60GB worth of Volume, you should get a new unallocated partition that is of size 60GB. Now we can proceed to flash our Ubuntu ISO image onto our USB drive.

<figure><img src=".gitbook/assets/image (6) (1).png" alt="" width="375"><figcaption><p>Final state after shrinking volume</p></figcaption></figure>

## Step 4: Flash Ubuntu ISO Image onto USB Drive

To flash the Ubuntu ISO Image onto our USB Drive, make sure that your USB Drive is connected to your USB Port.

**On Balena Etcher, click "Flash from file"**

<figure><img src=".gitbook/assets/image (7) (1).png" alt="" width="375"><figcaption><p>Balena Etcher Interface</p></figcaption></figure>

**Select Ubuntu ISO Image File**

<figure><img src=".gitbook/assets/image (8).png" alt="" width="375"><figcaption><p>Select ISO Image To Be Flashed</p></figcaption></figure>

**Click on "Select Target"**

<figure><img src=".gitbook/assets/image (9).png" alt="" width="375"><figcaption><p>Balena Etcher Interface</p></figcaption></figure>

**Select our USB Drive**

<figure><img src=".gitbook/assets/image (10).png" alt="" width="375"><figcaption><p>Select USB Drive</p></figcaption></figure>

**Lastly, click "Flash" to begin flash process**

<figure><img src=".gitbook/assets/image (11).png" alt="" width="375"><figcaption><p>Balena Etcher Interface</p></figcaption></figure>

You should see this after successfully flashing the ISO Image onto our USB Drive.

<figure><img src=".gitbook/assets/image (12).png" alt="" width="375"><figcaption><p>Completed Flash</p></figcaption></figure>

## Step 5: Restart and go into BIOS to Enable USB Boot

<mark style="color:red;">**This step will differ from each computer, but the overall objective is the same which is to enable USB Boot.**</mark>

Once we have flashed the Ubuntu ISO Image onto the USB Drive, we need to ensure that we have enabled USB Boot.

To do so, we restart our computer (while keeping the USB connected to your USB Port).

As the computer boots up, hold F10 to go into BIOS Setup.

<figure><img src=".gitbook/assets/image (13).png" alt="" width="375"><figcaption><p>Hold F10 to go into BIOS Setup</p></figcaption></figure>

Once in BIOS Setup, navigate to System Configurations -> Boot Options

<figure><img src=".gitbook/assets/image (14).png" alt="" width="375"><figcaption><p>Navigate to Boot Options in BIOS Setup</p></figcaption></figure>

After entering Boot Options, make sure the USB Boot is set to "Enabled".

<figure><img src=".gitbook/assets/image (15).png" alt="" width="375"><figcaption><p>Enable USB Boot</p></figcaption></figure>

Now that we have enabled USB Boot, save changes and restart the computer. \
This time holding F9 upon startup to launch the Boot Menu.

## Step 6: Launch Boot Manager and select USB drive to boot

To launch the Boot Manager, we hold F9 while our computer is starting up. Make sure that your USB Drive containing the Ubuntu ISO Image is connected.

<figure><img src=".gitbook/assets/image (16).png" alt="" width="375"><figcaption><p>Hold F9 to open Boot Menu</p></figcaption></figure>

In Boot Manager, select our USB Drive.

<figure><img src=".gitbook/assets/image (17).png" alt="" width="375"><figcaption><p>Boot Manager</p></figcaption></figure>

Now you should see the following interface, select "Try or Install Ubuntu".

<figure><img src=".gitbook/assets/image (19).png" alt="" width="375"><figcaption><p>Interface after booting from USB Drive</p></figcaption></figure>

Now you are ready to proceed to the final step to set up your Ubuntu Dual Boot.

## Step 7: Launch Ubuntu OS to install and setup

Congratulations, you are almost done with Ubuntu Dual Boot setup.

The final step is to install and complete the setup for Ubuntu.&#x20;

**1) Click on Install Ubuntu**

<figure><img src=".gitbook/assets/image (20).png" alt="" width="375"><figcaption></figcaption></figure>

**2) Select Normal Installation and Install third-party software**

<figure><img src=".gitbook/assets/image (21).png" alt="" width="375"><figcaption></figcaption></figure>

**3) For installation type, select Install Ubuntu alongside Windows Boot Manager**

This step will also automatically allocate the previously created partition to your Ubuntu OS.

<figure><img src=".gitbook/assets/image (23).png" alt="" width="375"><figcaption></figcaption></figure>

**4) Complete Installation**

<figure><img src=".gitbook/assets/image (27).png" alt="" width="375"><figcaption></figcaption></figure>

**5) Verify Setup Completion**

After restarting, you should see the following interface, now you can select Ubuntu or Windows upon every startup.

<figure><img src=".gitbook/assets/image (28).png" alt="" width="375"><figcaption></figcaption></figure>

Moreover, if you open up Disk Management in Windows, you should see that your 60GB partition is now allocated. This 60GB partition is allocated to your Ubuntu OS.

<figure><img src=".gitbook/assets/image (29).png" alt="" width="375"><figcaption></figcaption></figure>

With that, you are now ready to use Ubuntu on your Windows computer!
