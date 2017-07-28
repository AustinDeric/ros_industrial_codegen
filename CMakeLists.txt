cmake_minimum_required(VERSION 2.8.3)
project(ros_industrial_codegen)

find_package(catkin REQUIRED COMPONENTS
  rospy
  message_generation
)

add_service_files(FILES GenerateProgram.srv)

generate_messages()

catkin_package(
  CATKIN_DEPENDS
  message_runtime
  rospy
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

install(PROGRAMS
  scripts/generate_program_server.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

