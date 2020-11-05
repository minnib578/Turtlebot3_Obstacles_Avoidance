  # A Naive Obstacle Avoidance Technique for Turtlebot 3 implemented in ROS
The goal of this assignment is to get you started writing software that controls a (simulated) robot using ROS.
In this assignment you will create a ROS node that will drive the robot around with a simple wanderer algorithm, much like a Roomba robot vaccum cleaner. More specifically, the robot should move forward until it reaches an obstacle, then rotate in place until the way ahead is clear, then move forward again and repeat. 

## Introduction 
This is an obstacle avoidance technique simulated with Turtlebot 3 in Gazebo, ROS. The Turtlebot uses planar laser range-finder to detect obstacles in front as well as 15 degrees left and right from the front. Then based on the obstacle range, it either goes forward with linear velocity or, stops and rotates with angular velocity until it finds an obstacle-free path to go forward again.

## Pre-requisites
- Python 2
- ubuntu 18.04
- Installed ROS Melodic Morenia.
- [Turtlebot 3 simulation package](https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git)

## Installation and Create packages
if you installed catkin via apt-get for ROS melodic, excute following comand:
$ source /opt/ros/melodic/setup.bash

- Create catkin workspace
  ```
  $ mkdir -p ~/catkin_ws/src
  $ cd ~/catkin_ws/
  $ catkin_make
  $ source devel/setup.bash
  ```
  on the catkin workpsace, it should includes three folders:build,devel,src
  To make sure your workspace is properly overlayed by the setup script, make sure ROS_PACKAGE_PATH environment variable includes the directory you're in
  something should like this:
  ```
  $ echo $ROS_PACKAGE_PATH
  /home/youruser/catkin_ws/src:/opt/ros/kinetic/share
  ```
- Create ROS package
  ```
  $ cd ~/catkin_ws/src
  $ catkin_create_pkg wander_bot rospy geometry_msgs sensor_msgs
  
  # build the package on the catkin workspace:
  $ cd ~/catkin_ws
  $ catkin_make
  $ . ~/catkin_ws/devel/setup.bash
  ```
- Installed turtlebot3_simulations.
  ```
  $ cd ~/catkin_ws/src/
  $ git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
  $ cd ~/catkin_ws && catkin_make
  $ . ~/catkin_ws/devel/setup.bash
  $ export TURTLEBOT3_MODEL=burger
  ```

## Usage
  ```
  $ cd ~/catkin_ws
  $ catkin_make
  $ source devel/setup.bash
  $ roslaunch wander_bot wander_bot.launch
  ```


## Details
The launch folder includes the wander_bot.launch
The nodes folder includes the wander_bot node code
The src includes the init.py of wander_bot
Also there are CMakeLists.txt,package.xml and setup.py in wander_bot package.
In order to implemete avoiding the obstacles, we need to use rospy, geometry_msgs,and sensor_msgs packages

since the turtlebot3_world.launch file has already includes in wander_bot.launch file. To excute the code, you only need to do following action under terminal considering you have created a catkin workspace and installed all needed packages:
```
  $ cd ~/catkin_ws
  $ catkin_make
  $ source devel/setup.bash
  $ roslaunch wander_bot wander_bot.launch
  ```
Open other terminal and excute `rosmsg show LaserScan` and `rosmsg show Twist`, you would see the message formats

## Reference
1. http://wiki.ros.org/ROS/Tutorials
2. https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
3. http://gazebosim.org/tutorials?tut=ros_overview
4. https://github.com/enansakib/obstacle-avoidance-turtlebot.git
