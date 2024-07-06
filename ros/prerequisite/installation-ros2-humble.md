---
description: >-
  This page describes the ROS Installation Process for a specific ROS2
  version/distribution (ROS2 Humble).
---

# Installation \[ROS2 Humble]

{% hint style="danger" %}
Please make sure you have an Ubuntu 22.04 environment set up and ready to use.
{% endhint %}

### Which installation method should you choose?

Installing from binary packages or from source will both result in a fully-functional and usable ROS 2 install. Differences between the options depend on what you plan to do with ROS 2.

**Binary packages** are for general use and provide an already-built install of ROS 2. This is great for people who want to dive in and start using ROS 2 as-is, right away.

Linux users have two options for installing binary packages:

* Packages (debians or RPMS, depending on the platform)
* binary archive

Installing from packages is the recommended method, as it installs necessary dependencies automatically and also updates alongside regular system updates. However, you need root access in order to install Debian packages. If you don’t have root access, the binary archive is the next best choice.

Windows users who choose to install from binary packages only have the binary archive option (Debian packages are exclusive to Ubuntu/Debian).

**Building from source** is meant for developers looking to alter or explicitly omit parts of ROS 2’s base. It is also recommended for platforms that don’t support binaries. Building from source also gives you the option to install the absolute latest version of ROS 2.

***

For this guide, I will be focusing on the installation method based on installing ROS2 Humble through Debian Packages (Simplest Method).

All steps taken in this installation guide can be found from the official ROS2 Humble Installation Guide: [https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html)

1. Set locale

Make sure you have a locale which supports `UTF-8`. If you are in a minimal environment (such as a docker container), the locale may be something minimal like `POSIX`.&#x20;

Open up terminal using `Ctrl-Alt-T` and enter the following commands:

```
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

To verify locale settings:

```
locale  
```

2. Setup Sources (To access packages for download)

This step adds the ROS 2 apt repository to your system.

First ensure that the [Ubuntu Universe repository](https://help.ubuntu.com/community/Repositories/Ubuntu) is enabled.

```
sudo apt install software-properties-common
sudo add-apt-repository universe
```

Now add the ROS 2 GPG key with apt.&#x20;

```
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

Then add the repository to your sources list.

```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

3. Install ROS2 Packages

Update your apt repository caches after setting up the repositories.

```
sudo apt update
```

ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.

```
sudo apt upgrade
```

{% hint style="warning" %}
Due to early updates in Ubuntu 22.04 it is important that `systemd` and `udev`-related packages are updated before installing ROS 2. The installation of ROS 2’s dependencies on a freshly installed system without upgrading can trigger the **removal of critical system packages**.

Please refer to [ros2/ros2#1272](https://github.com/ros2/ros2/issues/1272) and [Launchpad #1974196](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1974196) for more information.
{% endhint %}

Desktop Install (Recommended): ROS, RViz, demos, tutorials.

```
sudo apt install ros-humble-desktop
```

This installation will take a while, good time to go for toilet break or get coffee.

Once installation is complete, it is good to understand how to properly set up our environment to work with ROS2 Humble.

4. Set up Environment

Before you use anything related to ROS, you have to <mark style="color:purple;">source</mark> this file.&#x20;

```
source /opt/ros/humble/setup.bash
```

The main function of running this is to set environment variables used by ROS, so we can run ROS stuff.&#x20;

You will need to do this for <mark style="color:yellow;">every terminal</mark>, but we have a trick that we can use to do that for us automatically.

Run the following command in your terminal and reopen your terminal. Now you won't need to run that command everytime you open up a new terminal!

```
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

{% hint style="info" %}
Fyi: .bashrc is a hidden file that is located in your home directory (denoted by \~) and this hidden file will be sourced everytime you open up a terminal.
{% endhint %}

Sourcing ROS 2 setup files will set several environment variables necessary for operating ROS 2. If you ever have problems finding or using your ROS 2 packages, make sure that your environment is properly set up using the following command:

```
printenv | grep -i ROS
```

Check that variables like `ROS_DISTRO` and `ROS_VERSION` are set. Below shows an example output. (need not be exactly the same as below)

```
ROS_VERSION=2
ROS_PYTHON_VERSION=3
ROS_DISTRO=humble
```

As you progress further, you may deal with even more ROS environment variables, so do be mindful of checking your environment variables!



Congratulations, you have now installed ROS2 Humble on your system!



I recommend going through the Official ROS2 Humble Tutorials to better understand ROS!

[https://docs.ros.org/en/humble/Tutorials.html](https://docs.ros.org/en/humble/Tutorials.html)\


Some key concepts that I encourage you to look into (recommended to go down the list one by one):

1. Nodes & Topics
2. Publishers & Subscribers
3. Services & Actions
4. ROS File Structure & How to Write Packages
5. Writing Launch Files
6. ROS Utilities such as `rqt, rqt_graph` for data inspection
7. How to record data using `ros2 bags`

