cmake_minimum_required(VERSION 3.0.2)
project(inverted_pendulum_rl_control)

find_package(catkin REQUIRED COMPONENTS
  rl_common
  rospy
  std_msgs
  message_generation
)

add_service_files(
  FILES
  SaveModel.srv
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

catkin_package()

catkin_install_python(PROGRAMS 
  scripts/train_ddpg.py
  scripts/eval_ddpg.py
  scripts/pid_control.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)
