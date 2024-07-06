# Image Common

{% embed url="https://wiki.ros.org/image_common" %}

In ROS (Robot Operating System), the image\_common stack provides a set of packages and tools for handling images in ROS. It facilitates the integration of cameras and image processing functionalities into ROS-based systems. Here are the primary components of the image\_common stack:

1. **image\_transport**:
   * Manages the transport of images in ROS.
   * Provides transparent compression/decompression for image topics.
   * Allows image data to be published and subscribed to using various transport methods (e.g., raw, compressed, theora).
2. **camera\_info\_manager**:
   * Manages camera calibration data.
   * Provides a standardized way to access and store camera calibration parameters.
   * Ensures that image data can be corrected for lens distortion and other camera-specific effects.
3. **camera\_calibration\_parsers**:
   * Reads and writes camera calibration parameters from files.
   * Supports various formats such as YAML and ini.
   * Facilitates easy loading and saving of camera calibration data.
4. **polled\_camera**:
   * Supports cameras that require polling to capture images.
   * Provides a mechanism for capturing images on demand rather than continuously.
5. **compressed\_image\_transport**:
   * Extends image\_transport to support compressed image formats.
   * Reduces the bandwidth required for transmitting image data by using JPEG or PNG compression.

<figure><img src="../../../.gitbook/assets/image (30).png" alt="" width="375"><figcaption><p>Packages that are included in image_common stack</p></figcaption></figure>
