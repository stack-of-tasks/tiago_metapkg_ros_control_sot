cmake_minimum_required(VERSION 2.6)

project(sot_tiago_bringup)

find_package(catkin REQUIRED)
catkin_package()

#set(PROJECT_NAME sot_tiago_bringup)
#set(PROJECT_DESCRIPTION ROS package for Stack of Tasks on Tiago)
#set(PROJECT_URL "")

#setup_project()

INSTALL(
  FILES 
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/config
)

INSTALL(
  FILES
  launch/geometric_simu.launch
  launch/geometric_simu_context.launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
)

INSTALL(
  FILES
  sot/tiago.yaml
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/sot
)

INSTALL(
  FILES
  package.xml
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/
)

#setup_project_finalize()

