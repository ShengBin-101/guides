# Image Pipeline

The image\_pipeline package fills the gap between getting raw images from a camera driver and higher-level vision processing.\
For more info about image\_pipeline: [http://wiki.ros.org/image\_pipeline](http://wiki.ros.org/image\_pipeline)

***

**Hardware Requirements**\
The image pipeline will work with any conforming ROS camera driver node.\
A ROS camera driver node should have the minimal requirements:

* Publishing topics ("/image\_raw" and "/camera\_info")
* Have the following service ("set\_camera\_info")

<figure><img src="../../../../.gitbook/assets/image.png" alt="" width="375"><figcaption><p>Topics published by ROS Camera Driver Node (eg. v4l2_camera_driver)</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (1).png" alt="" width="375"><figcaption><p>Minimal requirements of ROS camera driver nodes</p></figcaption></figure>

