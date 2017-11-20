cmake_minimum_required(VERSION 2.8.3)
project(ethercat)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED)

## System dependencies are found with CMake's conventions
# find_package(Boost REQUIRED COMPONENTS system)


## Uncomment this if the package has a setup.py. This macro ensures
## modules and global scripts declared therein get installed
## See http://ros.org/doc/api/catkin/html/user_guide/setup_dot_py.html
# catkin_python_setup()

################################################
## Declare ROS messages, services and actions ##
################################################

## To declare and build messages, services or actions from within this
## package, follow these steps:
## * Let MSG_DEP_SET be the set of packages whose message types you use in
##   your messages/services/actions (e.g. std_msgs, actionlib_msgs, ...).
## * In the file package.xml:
##   * add a build_depend tag for "message_generation"
##   * add a build_depend and a run_depend tag for each package in MSG_DEP_SET
##   * If MSG_DEP_SET isn't empty the following dependency has been pulled in
##     but can be declared for certainty nonetheless:
##     * add a run_depend tag for "message_runtime"
## * In this file (CMakeLists.txt):
##   * add "message_generation" and every package in MSG_DEP_SET to
find_package(catkin REQUIRED COMPONENTS
  roscpp
)


###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES mypkg
#  CATKIN_DEPENDS other_catkin_pkg
#  DEPENDS system_lib
)



## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
  include ${catkin_INCLUDE_DIRS}
# include
# ${catkin_INCLUDE_DIRS}
)


find_package(catkin REQUIRED COMPONENTS roscpp)
set(SOEM_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lib/SOEM)

message("${SOEM_DIR}")

add_subdirectory(lib/SOEM)
# add_subdirectory(src)




set(SOURCES src/infoslave.cpp)
set(BINARY slaver)
include_directories(${SOEM_DIR}/soem)
include_directories(${SOEM_DIR}/osal)
include_directories(${SOEM_DIR}/osal/linux)
include_directories(${SOEM_DIR}/oshw/linux)

add_executable(${BINARY} ${SOURCES})
add_dependencies(${BINARY} ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(${BINARY} soem ${catkin_LIBRAgit adRIES})
