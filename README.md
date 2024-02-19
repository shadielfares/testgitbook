---
description: >-
  This page will instruct you on properly preparing your development environment
  for ROS2 and WSLG.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Initial Setup

To begin, watch the following installation guide by MMRT **only up to 3:10,** then return back here**.**

<mark style="color:red;">**Note:**</mark> Upon approaching the **0:50 mark** of the video instead of `Ubuntu -18.04`_,_ please change the version number `18.04` to the latest version of Ubuntu you wish to install.

As of February 2024, the latest working version of Ubuntu with Windows 11 WSLG is `Ubuntu 22.04.3 LTS.`

### &#x20;

{% embed url="https://youtu.be/-_mZusYmJ8o?si=F3y4R7wTN-wu8WDH&t=5" %}

<mark style="color:orange;">Quick Tip</mark>: The `-y` appended at 2:30 passes through the `yes` value to the following prompted message that Ubuntu will ask you. This is an ease of accessibility trick and is useful to save some time!

At this point in the installation guide you will have your respective Ubuntu distro installed via WSLG.&#x20;

We will now proceed to install the current ROS2 packages. For reference, we will be using the [MMRT Maxwell repository](#user-content-fn-1)[^1] as our source of instruction, however you may continue with the following:&#x20;

Configuring `rosdep`

```
sudo apt update && sudo apt install python3-rosdep -y
sudo rosdep init
rosdep update
```

Clone this repo

```
git clone https://github.com/MacRover/maxwell.git
```

Use `rosdep` to install repo dependencies

```
cd maxwell/ros_ws
rosdep install --from-paths src --ignore-src -y
```

Build robot packages

```
colcon build --symlink-install
```

You have now completed the MMRT Initial Setup.





[^1]: [https://github.com/MacRover/maxwell#](https://github.com/MacRover/maxwell)
