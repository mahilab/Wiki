# CMake Primer

Definition from [CMake](https://cmake.org/): CMake is an open-source, cross-platform family of tools designed to build, test and package software. CMake is used to control the software compilation process using simple platform and compiler independent configuration files, and generate native makefiles and workspaces that can be used in the compiler environment of your choice. The suite of CMake tools were created by Kitware in response to the need for a powerful, cross-platform build environment for open-source projects such as ITK and VTK. 

There are several things specific to CMake, but we can start with typical CMake operations similar to other languages. 

The first thing to do when making a **CMakeLists.txt** file is setting the cmake minimum required version. That is done using the following command, and it is warned to use at least cmake 3.2.
~~~cmake
cmake_minimum_required(VERSION 3.5.0 FATAL_ERROR)
~~~

Next, you must set the name and version of the project you are working on. This is required, and it sill initialize several variables.
~~~cmake
project(<name> VERSION <version> LANGUAGES CXX)
~~~

Further projects can be created as sub-projects using the following function, where sourcedir is the path to your sub-project. 

~~~cmake
add_subdirectory(<sourcedir>)
~~~

To make sure that all projects can be built as a standalone project, or a subproject, make sure that you follow the following steps.
 - Don't modify global compile/link flags - for example, use ``target_include_directories`` instead of ``include_directories`` which will add those directories to a specific target.
 - Don't modify global compile/link flags
 - Dont make any global changes

~~~cmake 
find_package(MEL REQUIRED)
~~~

When you are ready to create an executable or libray, you can create them using the following commands. Note that both an executable and a library are targets.

If done properly, you should be able to find preinstalled dependencies, either generated by you, or generated by a different project.

## Running CMake
________________
CMake is run from the command line as follow: 

~~~shell
> cmake --build {build_directory} --target {target} --config {Release/Debug} --clean-first
~~~

