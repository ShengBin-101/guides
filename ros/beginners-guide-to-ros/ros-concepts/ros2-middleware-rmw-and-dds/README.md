---
description: Advanced
---

# ROS2 Middleware (RMW) and DDS

By default, ROS2 uses DDS as its [middleware](https://design.ros2.org/articles/ros_on_dds.html).&#x20;

Real Time Publish Subscribe protocol (RTPS) is a type of DDS protocol and it is used by ROS2.

Therefore, RMW is implemented using DDS, and DDS comes in various implementations depending on vendors.

ROS2 Build comes with the following vendors implementation of DDS:

* Eclipse Cyclone DDS
* eProsima Fast DDS
* RTI Connext DDS
* GurumNetworks GurumDDS

There are also non-dds implementation of RMW

* Zenoh

[https://docs.ros.org/en/humble/Installation/RMW-Implementations/Non-DDS-Implementations/Working-with-Zenoh.html](https://docs.ros.org/en/humble/Installation/RMW-Implementations/Non-DDS-Implementations/Working-with-Zenoh.html)&#x20;

### What is DDS (read more [here](https://design.ros2.org/articles/ros_on_dds.html)) <a href="#what-is-dds" id="what-is-dds"></a>

DDS provides a publish-subscribe transport which is very similar to ROS’s publish-subscribe transport. DDS uses the “Interface Description Language (IDL)” as defined by the [Object Management Group (OMG)](http://www.omg.org/) for message definition and serialization. DDS has a request-response style transport, which would be like ROS’s service system, in beta 2 as of June 2016 (called [DDS-RPC](http://www.omg.org/spec/DDS-RPC/)).

The default discovery system provided by DDS, which is required to use DDS’s publish-subscribe transport, is a distributed discovery system. This allows any two DDS programs to communicate without the need for a tool like the ROS master. This makes the system more fault tolerant and flexible. It is not required to use the dynamic discovery mechanism, however, as multiple DDS vendors provide options for static discovery.

### ROS Built on DDS <a href="#ros-built-on-dds" id="ros-built-on-dds"></a>

The goal is to make DDS an implementation detail of ROS 2. This means that all DDS specific APIs and message definitions would need to be hidden. DDS provides discovery, message definition, message serialization, and publish-subscribe transport. Therefore, DDS would provide discovery, publish-subscribe transport, and at least the underlying message serialization for ROS. ROS 2 would provide a ROS 1 like interface on top of DDS which hides much of the complexity of DDS for the majority of ROS users, but then separately provides access to the underlying DDS implementation for users that have extreme use cases or need to integrate with other, existing DDS systems.

![DDS and ROS API Layout](https://design.ros2.org/img/ros_on_dds/api_levels.png) _DDS and ROS API Layout_

***

In DDS, the primary mechanism for having different logical networks share a physical network is known as the Domain ID.

ROS 2 nodes on the same domain can freely discover and send messages to each other, while ROS 2 nodes on different domains cannot.

All ROS 2 nodes use domain ID 0 by default.

To avoid interference between different groups of computers running ROS 2 on the same network, a different domain ID should be set for each group.

The domain ID is used by DDS to compute UDP ports that will be used for discovery and communication. A UDP port is an unsigned 16-bit integer. Thus, the highest port number that can be allocated is 65535. See [this article](https://community.rti.com/content/forum-topic/statically-configure-firewall-let-omg-dds-traffic-through) for details on how the ports are computed.&#x20;

From the above article, the highest domain ID (short version) that can possibly be assigned is 232, while the lowest that can be assigned is 0.

{% hint style="info" %}
By default, the Linux kernel uses ports 32768-60999 for ephemeral ports. This means that domain IDs 0-101 and 215-232 can be safely used without colliding with ephemeral ports. The ephemeral port range is configurable in Linux by setting custom values in `/proc/sys/net/ipv4/ip_local_port_range`. If a custom ephemeral port range is used, the above numbers may have to be adjusted accordingly.
{% endhint %}

## What’s Happening Behind the Scenes When You Run ROS 2

When you run a **ROS 2 program**, it uses something called **DDS (Data Distribution Service)** to communicate. Each program (or **process**) joins a kind of network called a **domain**. To do this, it needs to use **network ports**—like phone lines on your computer for sending and receiving messages.

Every ROS 2 process on your computer grabs **2 "unicast" ports**. These ports are picked based on:

* The **domain ID** you're using (a number you assign),
* And the number of processes you've started on that domain.

Each new process uses the next available pair of ports.

### **The Problem: Limited Number of Ports**

Read more here: [Participant constraints](https://docs.ros.org/en/humble/Concepts/Intermediate/About-Domain-ID.html#id5)

Your computer has a limited number of ports. If you start **too many** ROS 2 processes, you can **run out of usable ports**, or worse, **start using ports that belong to other domains or the system** (called **ephemeral ports**). That can cause communication errors.

#### 🧠 Example 1: Safe Use with Domain ID 1

* First ROS 2 process uses ports 7660 and 7661.
* 120th process uses ports 7898 and 7899.
* **121st process** starts using ports that **belong to another domain** (domain ID 2), causing **conflicts**.

So, **limit yourself to about 120 ROS 2 processes per domain**, unless you're absolutely sure the computer will only use one domain.

***

#### ⚠️ Example 2: Problems at Higher Domain IDs

Domain ID numbers affect the port numbers too. Higher domain IDs use higher port numbers.

For example, on Linux:

* Domain ID 101 → First process uses port 32660.
* By the 54th process, ports go into the **"ephemeral port" range** (used by the system for temporary things like web browsing).
* **Don’t go past 54 processes** at domain ID 101, or things could break.

### **🧾 Simple Rules to Remember**

| Operating System                   | Safe Max Processes per Domain | Watch Out For                     |
| ---------------------------------- | ----------------------------- | --------------------------------- |
| Linux (low domain ID like 1)       | Up to 120 processes           | Above 120 causes domain overlap   |
| Linux (high domain ID like 101)    | Only 54 processes             | Above 54 enters system port range |
| macOS/Windows (high domain ID 166) | 120 processes                 | Same logic as Linux with low IDs  |
