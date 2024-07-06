# Disparity and Depth Image for Stereo Vision

## **Stereo processing using stereo\_image\_proc**

> **Stereo processing:** The [stereo\_image\_proc](http://wiki.ros.org/stereo\_image\_proc) node performs the duties of [image\_proc](http://wiki.ros.org/image\_proc) for a pair of cameras co-calibrated for stereo vision. It also uses stereo processing to produce disparity images and point clouds.

Disparity Image can be found using different algorithms, such as block-matching algorithm.

## Step 1: Obtain left and right camera calibration yaml files

Do this step if you have not gotten a yaml file from the camera calibration process.

```
ros2 run camera_calibration_parsers convert left.ini left.yml

ros2 run camera_calibration_parsers convert right.ini right.yml
```

## Step 2: Create launch file to run stereo\_image\_proc

Luckily, image\_pipeline provides a stereo\_image\_proc package that contains the launch file “stereo\_image\_proc.launch.py” that creates the following:

* debayer node and rectifier nodes to perform processing for left and right cameras
* disparity node that performs block matching to create disparity image (publishes to /disparity)
* pointcloud node that subscribes to /disparity and publishes pointcloud2 message which can be used to create 3D maps at a later stage\


stereo\_image\_proc.launch.py: launches stereo processing nodes + disparity node + pointcloud node



## Step 3: **Depth Processing using depth\_image\_proc**&#x20;

> **Depth processing:** [depth\_image\_proc](http://wiki.ros.org/depth\_image\_proc) provides nodelets for processing depth images (as produced by the [Kinect](http://wiki.ros.org/openni\_kinect), time-of-flight cameras, etc.), such as producing point clouds.\\

depth\_image\_proc provides basic processing for depth images, much as [image\_proc](https://wiki.ros.org/image\_proc) does for traditional 2D images

Some Examples:

<figure><img src="../../../../.gitbook/assets/image (4).png" alt="" width="375"><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (6).png" alt="" width="375"><figcaption></figcaption></figure>
