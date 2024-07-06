---
description: >-
  This page describes how to interpret PointCloud2 Data from LiDAR sensors and
  how they can be converted to custom representations using Point Cloud Library
  (pcl).
---

# Working with PointCloud2 Data

PointCloud2 is a common sensor message type used for point cloud data from LiDAR sensors. I will be using Ouster 0 - 64 Channel LiDAR and Ouster 2 - 128 Channel LiDAR for my explanations. These LiDARs are 3D LiDARs.

A 64 Channel LiDAR means the sensor has 64 laser emitters stacked on top of each other. So yes, a 128 Channel LiDAR will have 128 laser emitters stacked on top of each other. These laser emitters are then rotated about the central axis.&#x20;

<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>LiDAR Channel Types</p></figcaption></figure>

In the case of an Ouster 64-Channel LiDAR, at one timestamp, you will have a column of laser points and a column of laser reflections received by the sensor. Each receiver sensor will give a measurement for a single "point".&#x20;

With 64 "points" in this single instance, we obtain a "column" in a scan. As the emitters rotate, these "columns" are then stacked next to each other to form a 2D "picture".&#x20;

In one full revolution, this 2D "picture" obtained in the end is known as a "frame" and it contains all the measurements in a single revolution.&#x20;

All information about a single "frame" is then packaged into a single data structure called the PointCloud2 data structure.

Documentation on PointCloud2 Data Structure: [https://docs.ros.org/en/api/sensor\_msgs/html/msg/PointCloud2.html](https://docs.ros.org/en/api/sensor\_msgs/html/msg/PointCloud2.html)

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Compact Message Definition of PointCloud2 Data</p></figcaption></figure>



For an Ouster 0 - 64 Channel LiDAR operating at 1024x10 Mode (1024 divisions in one revolution and 10Hz Rotation Speed)

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption><p>Column-Diagram of PointCloud2 Data of an Ouster 0 - 64 Channel LiDAR</p></figcaption></figure>



Here is an example of a single timestamp of a LiDAR PointCloud2 Data of an Ouster 2 - 128 Channel LiDAR operating at (1024x10 Mode). Try to look at the PointCloud2 Data Documentation and see if you can decipher the data content!

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Visualisation of PointCloud2 Data of an Ouster 2 - 128 Channel LiDAR</p></figcaption></figure>

