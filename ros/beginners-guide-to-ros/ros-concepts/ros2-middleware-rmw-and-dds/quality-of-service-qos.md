# Quality of Service (QoS)

Quality of Service (QoS) policies allows us to tune communication between nodes.&#x20;

Setting the right policies can make ROS2 as reliable as TCP or as best-ffort as UDP.

ROS1 primarily supports TCP while ROS2 allows flexibility of underlying DDS transport in environment with lossy wireless networks where "best effort" policy is more suitable.

ROS2 can also be configured in real-time applications where there are strict deadlines.

{% hint style="info" %}
A set of QoS “policies” combine to form a QoS “profile”.
{% endhint %}

ROS 2 provides a set of predefined QoS profiles for common use cases (e.g. sensor data). At the same time, developers are given the flexibility to control specific policies of the QoS profiles.

## **QoS Policies**

<table><thead><tr><th width="132">QoS Policy</th><th width="184">Options</th><th>Description</th></tr></thead><tbody><tr><td><strong>History</strong></td><td><p>- <strong>Keep Last</strong></p><p>- <strong>Keep All</strong></p></td><td><p>Keep Last: Only stores the last N messages (defined by <strong>Depth</strong>).</p><p>Keep All: Stores all messages (limited by system resources).</p></td></tr><tr><td><strong>Depth</strong></td><td>Integer value</td><td><p>Size of the message queue. </p><p>Only applies when <strong>History = Keep Last</strong>.</p></td></tr><tr><td><strong>Reliability</strong></td><td><p>- <strong>Best Effort</strong></p><p>- <strong>Reliable</strong></p></td><td><p>Best Effort: May drop messages on weak networks.</p><p>Reliable: Ensures all messages are delivered, with retries.</p></td></tr><tr><td><strong>Durability</strong></td><td><p>- <strong>Volatile</strong></p><p>- <strong>Transient Local</strong></p></td><td><p>Volatile: Only new messages are received.</p><p>Transient Local: Subscribers can receive old messages sent before they joined.</p></td></tr><tr><td><strong>Deadline</strong></td><td>Duration (e.g., 100ms)</td><td><p>Max allowed time between messages. </p><p>If exceeded, a missed deadline is reported.</p></td></tr><tr><td><strong>Lifespan</strong></td><td>Duration</td><td>Max time a message remains valid after being published. Expired messages are dropped.</td></tr><tr><td><strong>Liveliness</strong></td><td><p>- <strong>Automatic</strong></p><p>- <strong>Manual by Topic</strong></p></td><td><p>Automatic: System manages liveliness when any message is published.</p><p>Manual: Publisher must actively signal it is still alive.</p></td></tr><tr><td><strong>Lease Duration</strong></td><td>Duration</td><td>Time limit for a publisher to assert it is alive. If exceeded, it's considered "not alive."</td></tr></tbody></table>

## QoS Profiles

Read more [here](https://docs.ros.org/en/humble/Concepts/Intermediate/About-Quality-of-Service-Settings.html)

| Profile               | Reliability   | Durability    | History     | Depth             | Liveliness     |                                                 |
| --------------------- | ------------- | ------------- | ----------- | ----------------- | -------------- | ----------------------------------------------- |
| **Default (Pub/Sub)** | Reliable      | Volatile      | Keep Last   | 10                | System Default | Matches ROS 1 behavior.                         |
| **Service**           | Reliable      | Volatile      | Keep Last   | 10                | System Default | Volatile avoids server getting old requests.    |
| **Sensor Data**       | Best Effort   | Volatile      | Keep Last   | Small (e.g., 5)   | System Default | Prioritizes timeliness over reliability.        |
| **Parameters**        | Reliable      | Volatile      | Keep Last   | Large (e.g., 100) | System Default | Large queue to prevent lost requests.           |
| **System Default**    | RMW-dependent | RMW-dependent | RMW-default | RMW-default       | RMW-default    | Uses underlying middleware’s built-in defaults. |

[Click here](https://github.com/ros2/rmw/blob/humble/rmw/include/rmw/qos_profiles.h) for the specific policies in use for the above profiles. The settings in these profiles are subject to further tweaks, based on the feedback from the community.

## QoS Compatibility

{% hint style="warning" %}
**All QoS policies must be compatible** for a connection to form.\
If even one is incompatible, **no messages will be exchanged**.
{% endhint %}

For more info: [click here](https://docs.ros.org/en/humble/Concepts/Intermediate/About-Quality-of-Service-Settings.html#qos-compatibilities)

#### **Compatibility of reliability QoS** **policies**_**:**_

| Publisher   | Subscriber  | Compatible? | Notes                                  |
| ----------- | ----------- | ----------- | -------------------------------------- |
| Best Effort | Best Effort | ✅ Yes       | Both willing to accept lossy delivery. |
| Best Effort | Reliable    | ❌ No        | Publisher can’t meet reliability.      |
| Reliable    | Best Effort | ✅ Yes       | Publisher offers more than needed.     |
| Reliable    | Reliable    | ✅ Yes       | Fully matched.                         |

#### **Durability Compatibility**

| Publisher       | Subscriber      | Compatible? | Message Availability       |
| --------------- | --------------- | ----------- | -------------------------- |
| Volatile        | Volatile        | ✅ Yes       | Only new messages          |
| Volatile        | Transient Local | ❌ No        | No communication           |
| Transient Local | Volatile        | ✅ Yes       | Only new messages          |
| Transient Local | Transient Local | ✅ Yes       | New + previously published |







