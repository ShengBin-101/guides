---
description: This page serves as a guide to work with ROS Bags on ROS2 Humble.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Working with ROS 1/2 Bags

There are some differences between ROS1 and ROS2 messages:&#x20;

{% embed url="https://design.ros2.org/articles/interface_definition.html" %}

## Understanding Bag Formats

**ROS1:**

* **Extension**: `.bag`
* **Storage**: Custom binary format
* **Tools**: `rosbag`, `rqt_bag`
* **Compression**: Supported (e.g., BZ2)
* **Metadata**: Topic names, types, timestamps

**ROS2:**

* **Extension**: `.db3`
* **Storage**: SQLite3 database
* **Tools**: `ros2 bag`
* **Compression**: Supported
* **Metadata**: More flexible and complex metadata

#### MCAP

**MCAP (Message Capture)**

* A proposed standard for a unified file format to store serialized messages for robotic systems.
* Designed to be flexible, efficient, and language-agnostic.
* Aims to standardize message storage across different middleware systems, improving interoperability and performance.

***

## How to play ROS2 Bags (.db3)?

### What should a rosbag file contain? <a href="#what-should-a-rosbag-file-contain" id="what-should-a-rosbag-file-contain"></a>

```
<bagfolder_name>
    |_ metadata.yaml
    |_ <bagfolder_name>.db3
```

### Playing rosbags that are .db3 files <a href="#playing-rosbags-that-are-.db3-files" id="playing-rosbags-that-are-.db3-files"></a>

{% code fullWidth="false" %}
```bash
Install plugins
sudo apt install ros-humble-rqt*
sudo apt install \ ros-humble-image-transport-plugins
```
{% endcode %}

Play Bag using any of the two commands:

```
ros2 bag play /path/to/bagfolder/bag.db3
```

```
ros2 bag play /path/to/bagfolder
```

Use rqt to view topics,

```
rqt
```

## How to use ROS1 Bags in ROS2?

You can use [rosbags-convert](https://ternaris.gitlab.io/rosbags/index.html) tool to unpack ROS1 .bag file to .db3 files that can be played using

`ros2 bag play </path/to/bag.db3>`&#x20;

If you want to obtain a .mcap file, we can use [rosbag2 to convert .db3 to .mcap](https://github.com/ros2/rosbag2/tree/rolling?tab=readme-ov-file#converting-bags).

### Extracting .db3 and metadata.yaml from .bag files

1.1) Install rosbags library

```
pip install rosbags
```

1.2) Navigate to directory containing .bag and extract .db3 and metadata

```
cd /path/to/bags
rosbags-convert --src /path/to/filename.bag --dst /path/to/output
```

If your terminal says "`rosbags-convert command not found`". It could be that your rosbags library is installed in a directory that is not included in PATH variable.

Go to your home directory and add the following line into \~/.bashrc. (Replace {user} with your device username)

```
export PATH=$PATH:/home/{user}/.local/bin
```

### Convert .db3 to .mcap

2.1) Ensure that you have rosbag2 installed

```bash
sudo apt-get install ros-humble-rosbag2
```

2.2) Write config file for conversion (name of file can differ)

```bash
vim convert.yaml
```

If you want your mcap file to contain all topics and services, write convert.yaml as such:

```bash
output_bags:
- uri: <NAME_OF_OUTPUT_DIR>
	storage_id: mcap
	all: true
```

2.3) Run command to convert

```bash
ros2 bag convert --input /path/to/bag --output-options /path/to/convert.yaml
```

***
