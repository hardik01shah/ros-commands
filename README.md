# ros-commands
This repo has all the important ros commands. 

## Setting up the workspace:
```sh
cd <path to catkin_ws>
catkin_make
source devel/setup.bash
roscore
```
## Creating a package:
```sh
catkin_create_pkg <package-name> <dependencies>
```
For e.g.
```sh
catkin_create_pkg test rospy nav_msgs sensor_msgs
```
## Running a file:
```sh
cd <path to folder containing the script>
```
Make an executable
```sh
chmod +x <script_name>
```
*Edit Cmakelists also and add the script name:*
>install(PROGRAMS<br>
>   scripts/*filename*<br>
>   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}<br>
> )<br>
Run
```
./<script_name>
```
or
```
rosrun <package name> <script name>
```
## Important for debugging:
To inspect what is being published on a topic:
```sh
rostopic echo /topicname
```
To view the rqt_graph
```sh
rosrun rqt_graph rqt_graph 
```
To view the tf_tree
```sh
rosrun rqt_tf_tree rqt_tf_tree
```
To view the statements passed using rospy.loginfo()
```sh
rostopic echo /rosout
```

## Gazebo:
```sh
rosrun gazebo_ros gazebo
```

## RViZ:
```sh
rosrun rviz rviz
```
For setting up the entire tf_tree for visualization of robot model in RViZ
```sh
rosrun robot_state_publisher robot_state_publisher
```
## Turtlebot3:
Installation
```sh
sudo apt-get install ros-melodic-turtlebot3-*
```
Run this command before every turtlebot3 command to set the model. <value> can be waffle_pi, waffle, burger
```sh
export TURTLEBOT3_MODEL=<value>
```
### SLAM Gmapping:
  Installation
  ```sh
  sudo apt-get install ros-melodic-slam-gmapping
  ```
  Launch
  ```sh
  roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
  ```
### Navigation:
  Installation
  ```sh
  sudo apt-get install ros-melodic-dwa-local-planner
  ```
  Launch
  ```sh
  roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=<path to map file>
  ```
  For e.g.
  ```sh
  roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=/home/hardik/map.yaml
  ```
### Launch in gazebo:
  ```sh
  roslaunch turtlebot3_gazebo turtlebot3_house.launch
  roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
  roslaunch turtlebot3_gazebo turtlebot3_world.launch
  ```
### Teleop Launch
  ```sh
  roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
  ```
## Rosbridge suite launch:
  Installation
  ```sh
  sudo apt-get install ros-<rosdistro>-rosbridge-server
  ```
  Check IP address
  ```sh
  hostname -I
  ```
  Launch
  ```sh
  roslaunch rosbridge_server rosbridge_websocket.launch
  ```
## Husky:
  Installation
  ```sh
  sudo apt-get install ros-melodic-husky-*
  ```
  Gazebo Launch
  ```sh
  roslaunch husky_gazebo husky_empty_world.launch
  roslaunch husky_gazebo husky_playpen.launch
  ```
  
