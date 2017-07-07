cmake_minimum_required(VERSION 2.8.3)
project(rtt_motor_action_msgs)

find_package(catkin REQUIRED COMPONENTS rtt_roscomm motor_action_msgs)

ros_generate_rtt_typekit(motor_action_msgs)
ros_generate_rtt_service_proxies(motor_action_msgs)

orocos_generate_package(
  DEPENDS motor_action_msgs
  DEPENDS_TARGETS rtt_roscomm
)
