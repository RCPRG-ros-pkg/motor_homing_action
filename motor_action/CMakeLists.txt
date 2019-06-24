# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(motor_action)

find_package(catkin REQUIRED COMPONENTS rtt_ros cmake_modules motor_action_msgs)

find_package(orocos_kdl REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(Boost COMPONENTS thread REQUIRED)

link_directories(
  ${orocos_kdl_LIBRARY_DIRS}
  )

include_directories(#include
  ${Boost_INCLUDE_DIR}
  ${catkin_INCLUDE_DIRS}
  ${orocos_kdl_INCLUDE_DIRS}
  ${Eigen3_INCLUDE_DIR}
  )

orocos_use_package( ocl-taskbrowser )
orocos_use_package( ocl-deployment )
orocos_use_package( ocl-logging )
orocos_use_package( rtt-typekit )

## Default component
orocos_component(motor_action src/motor_action.cpp)
target_link_libraries(motor_action ${catkin_LIBRARIES} ${USE_OROCOS_LIBRARIES} ${orocos_kdl_LIBRARIES})

orocos_generate_package(
  INCLUDE_DIRS include
  DEPENDS rtt_ros geometry_msgs std_msgs message_runtime rtt_roscomm
)

