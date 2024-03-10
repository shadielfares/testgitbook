---
description: >-
  This page will help you understand how the rover works between its software
  and electrical components.
---

# High-Level Overview

***

Additionally, this will assist as a visual aid.

<figure><img src="../.gitbook/assets/Screenshot 2024-03-09 182829.png" alt=""><figcaption></figcaption></figure>

The Rover utilizes a wide variety of Communication Protocols \[C.P] to perform its necessary functionalities. An important protocol that is used but will not be covered on this page will be **i2C**.&#x20;

This c.p is essential for transferring data between circuits using only two wires. For more information please visit the [I2C Onboarding page](../communication-protocol-i2c.md).

Familiarize yourselves with the following terms and be sure to understand their relationship to the overall functions of the Rover:

<mark style="color:red;">Note:</mark> The OBC will be the Jetson AGX Orin as of V2.

1.  "_OBC is the main communication hub for all subassemblies in the V2 rover._" \[1]&#x20;

    For your understanding, **many but not all** processes that occur throughout the rover are done through the OBC. Specifically regarding Infrared 3-D Image Processing, any AI inference tasks, and ... \[<mark style="color:blue;">ASK the squad for more</mark>]
2. CAN is the main method of communication used throughout the rover. Used for all drive and stepper motors and is used for all communication over the RADBOARD.&#x20;
3. RAD BOARD connects GPS, LORA



####

### Relevant Communication Protocols:

1. CAN
2. SPI

References:&#x20;

Only watch the following up to 2:50 for relevant information:&#x20;

{% embed url="https://www.youtube.com/watch?v=KV41WhjGgc0" %}
CANBUS Further Understanding Video
{% endembed %}

{% file src="../.gitbook/assets/Project_Spec_OBC.pdf" %}
OBC Documentation
{% endfile %}

{% file src="../.gitbook/assets/Project_Spec_RAD_V2.pdf" %}
RAD Documentation
{% endfile %}

Subscriber / Publisher Relationship:

One of the first concepts shown to you is how ROS operates between a subscriber node and a publisher node. This is incorporated in the&#x20;

