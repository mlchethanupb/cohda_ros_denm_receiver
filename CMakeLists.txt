cmake_minimum_required(VERSION 3.1.12)
project(cohda_ros_denm_receiver)

## Find catkin macros and libraries
find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  etsi_its_msgs
  # Add other necessary dependencies
)

## Declare a catkin package
catkin_package(
  CATKIN_DEPENDS roscpp std_msgs etsi_its_msgs # Add other necessary dependencies
)

## Build the node
include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  flatbuffers/include
)

add_executable(cohda_ros_denm_receiver src/denm_receiver.cpp)
add_dependencies(cohda_ros_denm_receiver etsi_its_msgs_generate_messages_cpp )
target_link_libraries(  cohda_ros_denm_receiver 
                        ${catkin_LIBRARIES} )
