Let us see in detail what a catkin package consists of - 

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

