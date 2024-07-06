# Monocular Image Processing

For image processing we can make use of the image\_pipeline packages:\
[https://github.com/ros-perception/image\_pipeline](https://github.com/ros-perception/image\_pipeline)

**Monocular processing (image processing on single camera)**

> **Monocular processing:** The raw image stream can be piped through the [image\_proc](http://wiki.ros.org/image\_proc) node to remove camera distortion. The node also performs color interpolation for Bayer pattern color cameras.

<figure><img src="http://wiki.ros.org/image_proc/cturtle?action=AttachFile&#x26;do=get&#x26;target=image_proc.png" alt="" height="89" width="582"><figcaption><p>Diagram showing image_proc node processing raw image from image_driver_node</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (2).png" alt="" width="375"><figcaption></figcaption></figure>

In image\_proc package, it contains Composable Nodes. Similar to Nodelets in ROS1, composable Nodes is a concept introduced in ROS 2 to provide a more flexible and scalable approach to building robotic systems. It allows nodes to be composed into a graph of interconnected components. \
Image\_proc contains composable nodes for the tasks of debayering and rectification. This allows image\_proc functions to be easily combined with other composable nodes, for example camera drivers or higher-level vision processing.&#x20;

In fact, the image\_proc launch file loads one debayer composable node and two rectify composable nodes as shown in the launch file below.&#x20;

For more info: [http://wiki.ros.org/image\_proc](http://wiki.ros.org/image\_proc)\


<figure><img src="../../../../.gitbook/assets/image (3).png" alt="" width="375"><figcaption><p>image_proc launch file</p></figcaption></figure>

Inside this `image_proc` launch file, it runs the two nodes below,\
\
1\. Debayer - Takes a raw camera stream and publishes monochrome and color versions of it. If the raw images are Bayer pattern, it debayers using bilinear interpolation.\
\
Subscribes to:\
/image\_raw\
Publishes:\
/image\_mono (monochrome image)\
/image\_color (color unrectified image)\
\
2\. Rectify - Takes an unrectified image stream and its associated calibration parameters, and produces rectified images.\
\
Subscribes to:\
/image\_mono (Unrectified image stream)\
/camera\_info (Camera metadata)\
Publishes:\
/image\_rect (Rectified image)\


