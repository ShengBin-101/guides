---
description: In this page, you will learn what is ROS, UNIX, Linux, Ubuntu.
---

# Prerequisites

## What is ROS?

Robot Operating System (ROS) is a set of software libraries and tools that help you build robot applications. Best part is it is open source (in programming terms its free-to-use for all).

{% hint style="warning" %}
Note, ROS is not an operating system.&#x20;

ROS is an open-source framework that provides a set of tools, libraries, and conventions for creating and running robotic applications. ROS is not an operating system in the traditional sense, but rather a collection of software modules that communicate through a standardized interface.&#x20;

For total beginners, just take it that ROS is the glue that puts different software modules together, making it easier to create software for robots.
{% endhint %}

Before learning ROS, you should be familiar with the following:

1. What is Ubuntu?
2. Unix Commands
3. Basic Programming Knowledge with Python/C++

***

## 1. What is UNIX/Linux/Debian/Ubuntu??

Let's address a common question everyone will have when they first try to use Linux:&#x20;

> What exactly is Ubuntu? What is Debian? What is Linux? What is UNIX?

### UNIX & Linux

**UNIX** is an older and very influential operating system that was first developed in the 1960s and 1970s at AT\&T's Bell Labs.&#x20;

**Linux** is an operating system, like Windows or macOS. An operating system is the software that manages all the hardware and software on a computer. It's what lets you interact with your computer and run applications.

While not directly derived from UNIX code, Linux was inspired by UNIX and follows many of its principles. Hence the command lines used in Linux is largely UNIX Command Lines.

_macOS is also a UNIX-based OS, hence the terminal works very similarly to that for Linux._

### Linux

Linux is special because it's open-source, meaning anyone can see its code, modify it, and share it with others. This has led to many different versions (or "distributions") of Linux being created.

### Debian

**Debian** is one of these Linux distributions. Think of it as a flavor of Linux. Just like there are different brands of cars, there are different brands of Linux, and Debian is one of them. Debian is known for its stability and the huge amount of software available for it. It serves as the foundation for other Linux distributions.

### Ubuntu

**Ubuntu** is another Linux distribution, and it's actually based on Debian. It's designed to be very user-friendly, especially for people who might be new to Linux. Ubuntu is popular because it’s easy to install and use, and it comes with a lot of helpful software right out of the box.

### Summary

* **Linux**: The underlying operating system.
* **Debian**: A stable and robust version (distribution) of Linux.
* **Ubuntu**: A user-friendly version of Linux that is based on Debian.

So, if you think of Linux as the basic model of a car, Debian is like a specific brand of that car, and Ubuntu is like a special version of that brand that's made to be especially easy to drive.

## 2. UNIX Commands

<mark style="color:yellow;">Minimally, you should know how to navigate directories using Command Lines.</mark>&#x20;

Here is a site that you can visit to learn about the [UNIX Commands](https://www.math.utah.edu/lab/unix/unix-tutorial.html).&#x20;

There are also plenty of videos on the internet teaching UNIX Commands.

Here are some videos that may help:

1. [Beginner's Guide To The Linux Terminal](https://www.youtube.com/watch?v=s3ii48qYBxA) (42mins)
2. [Linux File System/Structure](https://www.youtube.com/watch?v=HbgzrKJvDRw) (16 mins)

I believe best way to learn is to try it out for yourself! So you could follow my guides on [setting up Ubuntu 22.04](./#what-is-next) first!

## 3. Basic Programming Background (Python Minimally)

Minimally, you should be familiar with Python programming language.&#x20;

If not, you may visit [WS3 Schools (Python)](https://www.w3schools.com/python/).

My guides will mostly involve using Python, and occasionally C++ as not everything in ROS can be done in python. But don't worry, the pages within [Intro to ROS](../ros-installation/) will be done in Python.

However, if you have background in C++, you will have a better understanding of how ROS will work under the hood (especially the build process).&#x20;

***

## What is next?

Now that we have understood what is Ubuntu, we can now move on to setting up Ubuntu on our device(s).

For ROS, I strongly recommend using Ubuntu and specifically for this guide, Ubuntu 22.04.

Below are guides to set up Ubuntu for Windows. Sorry to all the mac users, I believe the internet has resources for that. (Maybe I'll add a guide in the future...)

{% content-ref url="ubuntu-setup-dual-booting-for-windows.md" %}
[ubuntu-setup-dual-booting-for-windows.md](ubuntu-setup-dual-booting-for-windows.md)
{% endcontent-ref %}

{% content-ref url="ubuntu-setup-windows-subsystem-for-linux-wsl.md" %}
[ubuntu-setup-windows-subsystem-for-linux-wsl.md](ubuntu-setup-windows-subsystem-for-linux-wsl.md)
{% endcontent-ref %}

