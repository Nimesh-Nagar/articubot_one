## Robot Package Template

It is recommended that you keep the repo/package name the same, but if you do change it, ensure you do a "Find all" using your IDE (or the built-in GitHub IDE by hitting the `.` key) and rename all instances of `articubot_one` to whatever your project's name is.

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).

## ROS and Gazebo Installation 

OS   : Ubuntu 20.04, 
ROS2 : Foxy  

Follow the steps as mentioned by clicking the link to install ROS2-Foxy on your Ubuntu(20.04) system : 
    https://docs.ros.org/en/foxy/Installation/Alternatives/Ubuntu-Development-Setup.html

**Steps for Installation of Gazebo** 

Step1 : `curl -sSL http://get.gazebosim.org | sh`    
Step2 : `echo “source /usr/share/gazebo-11/setup.bash ” >> ~/.bashrc`    
Setp3 : `gazebo`     

After Gazebo and ROS have been installed it is time to install the bridge between them. With this bridge you can launch gazebo within ROS and dynamically add models to Gazebo.      
Install gazebo_ros_pkgs as  `sudo apt install ros-foxy-gazebo-ros-pkgs`

**Add following paths in bashrc file**

open bashrc file `sudo nano ~/.bashrc`   
Now copy and paste following at the end of file. 

#ROS     
source /opt/ros/foxy/setup.bash    
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash

#Gazebo    
source /usr/share/gazebo-11/setup.bash


## Building Packages in ROS Workspace. 

