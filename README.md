# ROS Noetic Installation

ROS Noetic targets Ubuntu 20.04. There is also not a ROS1 distro that targets 22.04, and there never will be as Noetic is the last distro for ROS1.

Follow this for installing ROS Noetic
https://wiki.ros.org/noetic/Installation/Ubuntu    

# Creating a ROS workspace 
A Catkin workspace is a directory structure used in ROS (Robot Operating System) for organizing and building your ROS packages. It allows you to manage your code and dependencies effectively.
```
mkdir -p ~catkin_ws/src
cd ~/catkin_ws/
catkin_make
```
When you run catkin_make in the root of your Catkin workspace, it performs the following steps:

1. Configure the workspace: It detects all the packages in the src/ directory and sets up the necessary build environment.
2. Build the packages: It compiles the source code of the packages, resolving dependencies automatically.
3. Generate setup files: It creates or updates the setup files in the devel/ directory, which you can source to configure your terminal environment to use the newly built packages.

Before continuing source your new setup.*sh file:
```
source devel/setup.bash
```
This is a general structure of a catkin workspace - 

![image](https://github.com/user-attachments/assets/b05338dd-3a89-4703-91b9-b442f8a70f59)

# Navigating the ros filesystem

## Using rospack
rospack allows you to get information about packages.

Usage - 
```
rospack find [package_name]
```
this would return - 
```
YOUR_INSTALL_PATH/share/roscpp
```

## Using roscd

# Creating a rospackage 

What makes up a catkin package ?
For a package to be considered a catkin package it must meet a few requirements 

1. The package must contain a catkin compliant package.xml file

