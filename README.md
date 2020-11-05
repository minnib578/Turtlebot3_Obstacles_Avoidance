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
