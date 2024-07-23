---
description: >-
  This page will instruct you on properly preparing your development environment
  for ROS2 and WSLG.
---

# Initial Setup

To begin, watch the following installation guide by MMRT **only up to 3:10,** then return back here

{% hint style="info" %}
Upon approaching the **0:50 mark** of the video instead of `Ubuntu -18.04`_,_ please change the version number `18.04` to the latest version of Ubuntu you wish to install.
{% endhint %}

As of February 2024, the latest working version of Ubuntu with Windows 11 WSLG is `Ubuntu 22.04.3 LTS.`

{% embed url="https://youtu.be/-_mZusYmJ8o?si=F3y4R7wTN-wu8WDH&t=5" %}

{% hint style="info" %}
<mark style="color:orange;">Quick Tip</mark>:  The `-y` appended at 2:30 passes through the `yes` value to the following prompted message that Ubuntu will ask you. This is an ease of accessibility trick and is useful to save some time!
{% endhint %}

At this point in the installation guide, you will have your respective Ubuntu distro installed via WSLG.

Now we will proceed with installing Ros-2-Iron-Irwini. Instructions follow their official doc's page:&#x20;

{% tabs %}
{% tab title="Set Locale" %}
```
locale # check for UTF-8
sudo apt update && sudo apt install locales sudo locale-gen en_US en_US.UTF-8 sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 export LANG=en_US.UTF-8
locale # verify settingsSet Locale
```
{% endtab %}

{% tab title="Enable Required Repositories" %}
```
sudo apt install software-properties-common sudo add-apt-repository universe 
```
{% endtab %}

{% tab title="Enable Required Repositories (2)" %}
```
sudo apt update && sudo apt install curl -y sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
{% endtab %}

{% tab title="Enable Required Repositories (3)" %}
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
{% endtab %}

{% tab title="Optional: Development Tools" %}
```
sudo apt update && sudo apt install ros-dev-tools
```
{% endtab %}

{% tab title="Installing Ros2" %}
```
sudo apt update && sudo apt upgrade -y
```
{% endtab %}

{% tab title="Install Ros2 (2)" %}
```
sudo apt install ros-iron-desktop
```
{% endtab %}

{% tab title="Install Ros2 (3)" %}
```
sudo apt install ros-iron-ros-base
```
{% endtab %}

{% tab title="Setting Up Environment" %}
```
nano .bashrc 
```
{% endtab %}

{% tab title="Setting Up Environment (2)" %}
\#Scroll down with the arrow keys all the way to the bottom of the file and paste the following command:&#x20;

After pasting: CRTL+S, CTRL+X

```
source /opt/ros/iron/setup.bash
```
{% endtab %}
{% endtabs %}

We will now proceed to install the current ROS2 packages. For reference, we will be using the [MMRT Maxwell repository](#user-content-fn-1)[^1] as our source of instruction, however, you may continue with the following:

{% tabs %}
{% tab title="Configuring rosdep" %}
Configuring `rosdep`

```
sudo apt update && sudo apt install python3-rosdep2 -y
sudo rosdep init
rosdep update
```
{% endtab %}

{% tab title="Cloning Repo" %}
Clone this repo

```
git clone https://github.com/MacRover/maxwell.git
```
{% endtab %}

{% tab title="Dependencies" %}
Use `rosdep` to install repo dependencies

```
cd maxwell/ros_ws
rosdep install --from-paths src --ignore-src -y
```
{% endtab %}

{% tab title="Colon Build" %}
```
colcon build --symlink-install
```
{% endtab %}
{% endtabs %}

You have now completed the MMRT Initial Setup.

[^1]: [https://github.com/MacRover/maxwell#](https://github.com/MacRover/maxwell)
