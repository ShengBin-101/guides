# Camera Calibration

**1) Calibrate camera using camera\_calibration package**\
[http://wiki.ros.org/camera\_calibration](http://wiki.ros.org/camera\_calibration)

> **Calibration:** Cameras must be calibrated in order to relate the images they produce to the three-dimensional world. The [camera\_calibration](http://wiki.ros.org/camera\_calibration) package provides tools to calibrate monocular and stereo cameras in your ROS system. A [CameraInfo wiki page](http://wiki.ros.org/image\_pipeline/CameraInfo) provides a detailed description of the parameters used by the pipeline.

Intrinsic Calibration of single Cameras gives us the Camera Matrix which contains information on how to undistort warping in camera lenses.&#x20;

<figure><img src="../../../.gitbook/assets/image (2).png" alt="" width="375"><figcaption><p>Example of Undistortion using camera_info</p></figcaption></figure>



**2) Stereo Calibration using camera\_calibration package**

If you intend on using two front facing cameras to perform stereo vision to obtain depth information, you need to perform stereo calibration to obtain the transform between two cameras. This is known as extrinsic calibration. This can also be done using camera\_calibration package in ROS.&#x20;

For more info:

{% embed url="https://wiki.ros.org/camera_calibration/Tutorials/StereoCalibration" %}

