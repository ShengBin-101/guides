---
description: '[Advanced]'
---

# Choosing DDS/RTPS Implementation

There are many factors you might consider while choosing a middleware implementation: logistical considerations like the license, or technical considerations like platform availability, or computation footprint.

Vendors may provide more than one DDS or RTPS implementation targeted at meeting different needs.

#### Supported DDS Implementations and RMWs

| Vendor                     | License             | RMW Package          | Status                       |
| -------------------------- | ------------------- | -------------------- | ---------------------------- |
| **eProsima Fast DDS**      | Apache 2            | `rmw_fastrtps_cpp`   | Full support (default)       |
| **Eclipse Cyclone DDS**    | EPL v2.0            | `rmw_cyclonedds_cpp` | Full support                 |
| **RTI Connext DDS**        | Commercial/Research | `rmw_connextdds`     | Full support (needs install) |
| **GurumNetworks GurumDDS** | Commercial          | `rmw_gurumdds_cpp`   | Community support            |

***

**Using Multiple RMW Implementations**

* ROS 2 binaries include support for several RMWs by default.
* Fast DDS is the **default**.
* You can switch to other RMWs without rebuilding ROS 2, just by setting environment variables.
* If building from source, multiple RMWs can be built at once if dependencies are available.

***

#### Cross-Vendor Compatibility Notes

* Not all DDS implementations can talk to each other reliably.
* Known issues:
  * **Fast DDS ↔ Connext**: WString issue on macOS
  * **Connext ↔ Cyclone DDS**: WString communication not supported
* Best practice: **Use the same RMW across your entire system**.

***

#### Default RMW Selection

* If `rmw_fastrtps_cpp` is installed, it’s used by default.
* Otherwise, the default is the **alphabetically first** installed RMW package.







