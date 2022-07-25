# SM2022_AI_Task-02
# Installing package arduino robot arm in ROS
This repo aims to describe step by step tutorial on arduino robot arm with ROS package in Ubuntu 20.04
<br>

![01](https://user-images.githubusercontent.com/101488769/180624681-b26da4fc-7f29-4c71-8dc4-968524c12055.jpg)
<br>

### Table of Contents
* [1- Installing-ROS](#1-Installing-ROS)
* [2- Installing package arduino robot arm](#2-Installing-package-arduino-robot-arm)


<br>

## 1-Installing-ROS
### 1.1 Installation
Install the `ros-noeitic-ros-base` package following these directions:
* ROS Noetic - [ROS Install Instructions](http://wiki.ros.org/Installation/Ubuntu)
<br>


### 1.2 Video to help
https://www.youtube.com/watch?v=ZA7u2XPmnlo&t=106s
<br>
<br>


### 1.3 Testing
Before proceeding, if you're using ROS Noetic make sure that `roscore` is running first:

```bash
$ roscore
```
![Task 01 1](https://user-images.githubusercontent.com/101488769/176632070-d9e8a783-d149-4c0d-8739-6081b1bb2c2f.png)
<br>

## 2-Installing-package-arduino-robot-arm
### 2.1 Installation
Install the `robot-arm-with-ros-noeitic` package following these directions:

```sudo apt-get install ros-noetic-catkin```

```mkdir -p ~/catkin_ws/src```

```cd ~/catkin_ws/```

```catkin_make```

```cd ~/catkin_ws/src```

```git clone https://github.com/smart-methods/arduino_robot_arm.git```

```cd ~/catkin_ws```

<b>Dependencies:</b>
<br>
run this instruction inside your workspace:

```$ rosdep install --from-paths src --ignore-src -r -y```

make sure you installed all these packages:

for noetic distro
```
$ sudo apt-get install ros-noetic-moveit
$ sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
$ sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control
```
<b> Note : </b> The remainder of the instruction suggest you watch the video below

```sudo nano ~/.bashrc```  

or you may use another command to open the file as a note :  
```gedit ~/.bashrc```

at the end of the (bashrc) file add the follwing line (don't forget to Change "YourOSName") :  
```source /home/YourOSName/catkin_ws/devel/setup.bash```  

 ![image](https://user-images.githubusercontent.com/107868473/180746894-c273994b-7dd8-4da5-a91b-5fce9fa6d588.png)

then save it by:  
* using the first line : clicking `ctrl + o` then "Enter" then `ctrl + x`
* using the second line : saving it normally .  

finally , use the following line to update the "bashrc" file :  
```source ~/.bashrc```

<b> 

### 2.2 Video to help
https://youtu.be/fr6TXEd2rXI?t=513
<br>
<br>

<b> 

## 2.3 Testing
 (You may have a look at the _videos folder_ after this section)  
### Controlling the robot arm by joint_state_publisher:
run the line :  
```bash
$ roslaunch robot_arm_pkg check_motors.launch
```
![02](https://user-images.githubusercontent.com/101488769/180625511-4797f937-1701-4f02-8591-de9319a99c3b.png)<br>

don't forget to connect with hardware by running the following line in a new terminal :  
```bash
$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```
<br>
<br>
<br>

### Controlling the robot arm by Moveit and kinematics:
run the line :  
```bash
$ roslaunch moveit_pkg demo.launch
```
![image](https://user-images.githubusercontent.com/107868473/180745800-86f22bdf-2d78-4ce8-bb9b-50e4bf8f126a.png)

also connect with hardware by running run the following line :
```bash
$ rosrun rosserial_python serial_node.py _port:=/dev/ttyUSB0 _baud:=115200
```
