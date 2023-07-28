# Object Detection and Obstacle Avoidance Robot

It is recommended that you keep the repo/package name the same, but if you do change it, ensure you do a "Find all" using your IDE (or the built-in GitHub IDE by hitting the `.` key) and rename all instances of `articubot_one` to whatever your project's name is.

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).

## ROS and Gazebo Installation 

OS   :   Ubuntu 20.04 , ROS2 : Foxy  

Follow the steps as mentioned by clicking the link to install ROS2-Foxy on your Ubuntu(20.04) system : 
    https://docs.ros.org/en/foxy/Installation/Alternatives/Ubuntu-Development-Setup.html

**Steps for Installation of Gazebo**

* Step1 : `curl -sSL http://get.gazebosim.org | sh`    
* Step2 : `echo “source /usr/share/gazebo-11/setup.bash ” >> ~/.bashrc`    
* Setp3 : `gazebo`     

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

* **Install xacro and joint state publisher gui** 
```   
sudo apt install ros-foxy-xacro ros-foxy-joint-state-publisher-gui 
```  

* **Install SLAM Tool-Box and ROS2 Navigation packages**    
``` 
sudo apt install ros-foxy-slam-toolbox
```

```
sudo apt install ros-foxy-navigation2 ros-foxy-nav2-bringup ros-foxy-turtlebot3*        
```
## Building Packages in ROS Workspace. 

*Create workspace*  :   `mkdir -p dev_ws/src && cd dev_ws/src `    
Now Clone this repo :   `git clone <url> `  
Go back to dev_ws   :   `cd ../`    
Enter Command       :   `colcon build --symlink-install `

#
## Steps to Run this Project

* Below command will Spawn the `robot` and our `Maze World` into `Gazebo Simulator`. 

``` 
ros2 launch articubot_one launch_sim.launch.py world:=./src/articubot_one/worlds/maze.world 
```

* Below command will launch slam-toolbox and previously saved mappper file. 

```
ros2 launch slam_toolbox online_async_launch.py params_file:=./src/articubot_one/config/mapper_online_async_maze.yaml use_sim_time:=true
```

* Below command will launch Nav2 stack of ROS2.  

```
ros2 launch nav2_bringup navigation_launch.py use_sim_time:=true
```

* Following command will launch Rviz with previously saved configurations.

```
rviz2 -d ./src/articubot_one/config/maze_conf.rviz
```




