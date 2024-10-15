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

### Package.xml file

This file defines properties about the package such as the package name, version numbers, authors, maintainers, and dependencies on other catkin packages. 

There are a minimal set of tags that need to be nested within the <package> tag to make the package manifest complete.

<name> - The name of the package
<version> - The version number of the package (required to be 3 dot-separated integers)
<description> - A description of the package contents
<maintainer> - The name of the person(s) that is/are maintaining the package
<license> - The software license(s) (e.g. GPL, BSD, ASL) under which the code is released.

The package manifest with minimal tags does not specify any dependencies on other packages. Packages can have six types of dependencies:

#### Dependencies 

Package can have six types of dependencies -

Build Dependencies specify which packages are needed to build this package. This is the case when any file from these packages is required at build time. This can be including headers from these packages at compilation time, linking against libraries from these packages or requiring any other resource at build time (especially when these packages are find_package()-ed in CMake). In a cross-compilation scenario build dependencies are for the targeted architecture.

Build Export Dependencies specify which packages are needed to build libraries against this package. This is the case when you transitively include their headers in public headers in this package (especially when these packages are declared as (CATKIN_)DEPENDS in catkin_package() in CMake).

Execution Dependencies specify which packages are needed to run code in this package. This is the case when you depend on shared libraries in this package (especially when these packages are declared as (CATKIN_)DEPENDS in catkin_package() in CMake).

Test Dependencies specify only additional dependencies for unit tests. They should never duplicate any dependencies already mentioned as build or run dependencies.

Build Tool Dependencies specify build system tools which this package needs to build itself. Typically the only build tool needed is catkin. In a cross-compilation scenario build tool dependencies are for the architecture on which the compilation is performed.

Documentation Tool Dependencies specify documentation tools which this package needs to generate documentation.

These six types of dependencies are specified using the following respective tags:

1. <depend>  - specifies that a dependency is a build, export, and execution dependency. This is the most commonly used dependency tag.
2. <build_depend> - If you only use some particular dependency for building your package, and not at execution time, you can use the <build_depend> tag. For example, the ROS angles package is categoized as build_depend because it provides functionality which is only needed in build process rather than runtime. It doesn't have any runtime executables or nodes that need to be running when your package is executed.
3. <build_export_depend>
4. <exec_depend>
5. <test_depend>
6. <buildtool_depend>
7. <doc_depend>

All packages have at least one dependency

#### Additional tags 

<url> - A URL for information on the package, typically a wiki page on ros.org.
<author> - The author(s) of the package
