cmake_minimum_required(VERSION 2.8.3)
project(imu_driver)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  message_generation 
  dynamic_reconfigure
  rosconsole
  roscpp_serialization 
  roslib 
  rostime
  sensor_msgs
  serial
)



#add_message_files(FILES
#  JY901_frame.msg
#  Mile.msg
#  Control.msg
#)

#generate_messages(DEPENDENCIES
#  std_msgs
#)

catkin_package(
 INCLUDE_DIRS src
 CATKIN_DEPENDS serial roscpp sensor_msgs tf
 DEPENDS system_lib
 message_runtime 
)

include_directories(
	include 
	${catkin_INCLUDE_DIRS}
)

add_executable(imu_node
  src/imu_decoder.cpp
)

target_link_libraries(imu_node
  #serial
  ${catkin_LIBRARIES}
)

