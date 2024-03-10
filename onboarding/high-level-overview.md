---
description: >-
  This page will help you understand how the rover works between its software
  and electrical components.
---

# High-Level Overview

***

<figure><img src="../.gitbook/assets/Screenshot 2024-03-09 182829.png" alt=""><figcaption><p>Reference Board [1]</p></figcaption></figure>

The Rover utilizes a wide variety of Communication Protocols \[C.P] to perform its necessary functionalities. An important protocol that is used but will not be covered on this page will be **i2C**.&#x20;

This c.p is essential for transferring data between circuits using only two wires. For more information please visit the [I2C Onboarding page](../communication-protocol-i2c.md).

Familiarize yourselves with the following terms and be sure to understand their relationship to the overall functions of the Rover:

{% hint style="info" %}
The OBC will be the Jetson AGX Orin as of V2.
{% endhint %}

1.  The On-Board Controller, better known as OBC "..._is the main communication hub for all subassemblies in the V2 rover._" \[2]&#x20;

    For your understanding, **many but not all** processes that occur throughout the rover are done through the OBC. Specifically regarding Infrared 3-D Image Processing, any AI inference tasks, and ... \[<mark style="color:blue;">ASK the squad for more</mark>]
2. CAN is the main method of communication used throughout the rover. Used for all drive and stepper motors and is used for all communication over the RADBOARD. CANBUS is the process by which information is delivered through 8 or 64-byte packets_._ For reference, many physical wires on the board use CAN, however, you can further determine the exact protocol by referring to \[1] for specific cases.&#x20;
3. RAD BOARD connects the GPS and LoRa \[INCLUDE MORE ]using a Reader, Writer Architecture similar to [ROS2's structure](https://docs.ros.org/en/iron/index.html).&#x20;

For example, if we would like the current position of the rover, the two components we need to focus on are the RADBOARD and GPS.

***

Writer:

RADBOARD: Using CANBUS creates a ros-topic looking for the current GPS location.

Reader:

GPS: Receives the sent node asking for the GPS location and sends it back to the RADBOARD.

This reader-writer relationship goes both ways to allow for safe and effective communication. The trend will always be **request and confirmation**.

### Briefly on Communication Protocols:

We can now understand that CAN is used on inter-board basis, however what do we use to actually have micro-controllers and additional peripherals **on the same board?**

This would be the Serial Peripheral Interface \[SPI] c.p.&#x20;

SPI offers a similar Master / Slave Architecture to [I2C ](../communication-protocol-i2c.md)however as previously stated only exists within each respective board.&#x20;

For example.. \[<mark style="color:blue;">ASK THE SQUAD</mark>]



References:&#x20;

Only watch the following up to 2:50 for relevant information:&#x20;

{% embed url="https://www.youtube.com/watch?v=KV41WhjGgc0" %}
CANBUS Further Understanding Video
{% endembed %}

If you'd like to understand how CANBUS works at a greater level, it is similar in architecture to Ethernet TCP protocol, which you may learn more about here.

[https://www.youtube.com/watch?v=PpsEaqJV\_A0](https://www.youtube.com/watch?v=PpsEaqJV\_A0)

{% file src="../.gitbook/assets/Project_Spec_OBC.pdf" %}
OBC Documentation
{% endfile %}

{% file src="../.gitbook/assets/Project_Spec_RAD_V2.pdf" %}
RAD Documentation
{% endfile %}

