---
description: >-
  In this segment, we will first understand the different versions of ROS and
  also what are ROS distributions.
---

# ROS Installation

## Prerequisite: Get Ubuntu

ROS is best used with an Ubuntu environment. For my guides, I am using Ubuntu 22.04 (Dual Booted on Windows). For information on how to do that, refer to the below guide.

{% content-ref url="../prerequisites/ubuntu-setup-dual-booting-for-windows.md" %}
[ubuntu-setup-dual-booting-for-windows.md](../prerequisites/ubuntu-setup-dual-booting-for-windows.md)
{% endcontent-ref %}

Another good alternative (and easier to setup) is to use Windows Subsystem for Linux (WSL) and specifically WSL version 2 (WSL2).

{% content-ref url="../prerequisites/ubuntu-setup-windows-subsystem-for-linux-wsl.md" %}
[ubuntu-setup-windows-subsystem-for-linux-wsl.md](../prerequisites/ubuntu-setup-windows-subsystem-for-linux-wsl.md)
{% endcontent-ref %}

## What version of ROS should I use?&#x20;

There are two top-level versions of ROS.

1. ROS1
2. ROS2

Both works to create and program robots. I'd recommend you to learn both ROS1 and ROS2 to be familiar with the differences.&#x20;

Sometimes we just refer our default ROS version as "ROS" so just take note that when I mention "ROS" in subsequent pages, I am referring to ROS2.

What is the main difference? Here is a link to describe the differences between the two.&#x20;

{% embed url="https://www.model-prime.com/blog/ros-1-vs-ros-2-what-are-the-biggest-differences" %}

But the confusion doesn't just end here, there are different versions for ROS1 and ROS2 respectively too. They are called distributions/distros and new ones come out every 2-4 years.

**ROS1 Distributions**

{% embed url="https://wiki.ros.org/Distributions" %}

**ROS2 Distributions**&#x20;

{% embed url="https://docs.ros.org/en/jazzy/Releases.html" %}

For my guides, I will be using ROS2, specifically the Humble Distribution.

Note that distributions require specific Ubuntu Distros! For example, ROS2 Humble works on Ubuntu 22.04.&#x20;

***

So now that you have a brief understanding of ROS, let us take a look at how we can set up ROS.&#x20;

{% content-ref url="installation-guide-ros2-humble.md" %}
[installation-guide-ros2-humble.md](installation-guide-ros2-humble.md)
{% endcontent-ref %}

