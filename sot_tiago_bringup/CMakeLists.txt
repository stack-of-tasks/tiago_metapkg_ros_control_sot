cmake_minimum_required(VERSION 2.6)

project(sot_tiago_bringup)

find_package(catkin REQUIRED)
catkin_package()

#set(PROJECT_NAME sot_tiago_bringup)
#set(PROJECT_DESCRIPTION ROS package for Stack of Tasks on Tiago)
#set(PROJECT_URL "")

#setup_project()

INSTALL(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

INSTALL(
  FILES
  package.xml
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/
)

#setup_project_finalize()

