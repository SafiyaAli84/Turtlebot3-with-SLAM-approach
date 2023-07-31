# Turtlebot3-with-SLAM-approach

# Requirements

- Oracle VM VirtualBox Manager version 7.0

- Ubuntu-18.04.6-desktop-amd64.iso

- ROS melodic

# Install ROS on Remote PC

```linux
$sudo apt update
$sudo apt upgrade
$wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh
$chmod 755 ./install_ros_melodic.sh 
$bash ./install_ros_melodic.sh
```

# Install Dependent ROS Packages
```linux
$ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
```

# Install TurtleBot3 Packages

```linux
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3
```

# Set TurtleBot3 Model Name

``` linux
$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
```

# Execute Gazebo

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslunch turtlebot3_gazebo turtlebot3_world.lunch
```
![safiya  Running  - Oracle VM VirtualBox 7_30_2023 7_24_00 PM](https://github.com/SafiyaAli84/Turtlebot3-with-SLAM-approach/assets/140127999/31c3c0d4-af44-439b-bfb7-a2ce97b7ba25)

# Execute SLAM 
In this case, we use gmapping that is general slam package.

File> New Tap

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```

![safiya  Running  - Oracle VM VirtualBox 7_30_2023 7_30_57 PM](https://github.com/SafiyaAli84/Turtlebot3-with-SLAM-approach/assets/140127999/9726d54f-ae6b-4480-8b28-7f2d0e515d47)

# Execute keypad

File> New Tap

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

# Map output

File> New Tap

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$rosrun map_server map_saver -f ~/map
```
out and close terminal ( Execute keypad ) and ( Execute SLAM ).

# Activate Gazebo

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```

![safiya  Running  - Oracle VM VirtualBox 7_31_2023 9_17_40 AM](https://github.com/SafiyaAli84/Turtlebot3-with-SLAM-approach/assets/140127999/2cf39f76-4cb6-4b58-a61d-71fc5b2865dc)











