cmake_minimum_required(VERSION 2.8.3)
project(robotiq_s_model_articulated_gazebo_plugins)

find_package(catkin REQUIRED COMPONENTS std_msgs gazebo_plugins actionlib tf image_transport control_msgs trajectory_msgs geometry_msgs sensor_msgs roscpp gazebo_ros robotiq_s_model_articulated_msgs robotiq_s_model_control)

find_package(gazebo REQUIRED)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${GAZEBO_INCLUDE_DIRS}
)

link_directories(
  ${GAZEBO_LIBRARY_DIRS}
)

catkin_package(
   DEPENDS gazebo_plugins gazebo_ros robotiq_s_model_articulated_msgs roscpp robotiq_s_model_control
)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

add_library(RobotiqHandPlugin src/RobotiqHandPlugin.cpp)
set_target_properties(RobotiqHandPlugin PROPERTIES LINK_FLAGS "${ld_flags}")
set_target_properties(RobotiqHandPlugin PROPERTIES COMPILE_FLAGS "${cxx_flags}")
target_link_libraries(RobotiqHandPlugin ${catkin_LIBRARIES})
add_dependencies(RobotiqHandPlugin robotiq_s_model_articulated_msgs_gencpp)
add_dependencies(RobotiqHandPlugin robotiq_s_model_control_gencpp)

install(TARGETS RobotiqHandPlugin DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}/${PROJECT_NAME}/plugins/)


add_library(RobotiqHandPlugin_controlMsg src/RobotiqHandPlugin_controlMsg.cpp)
set_target_properties(RobotiqHandPlugin_controlMsg PROPERTIES LINK_FLAGS "${ld_flags}")
set_target_properties(RobotiqHandPlugin_controlMsg PROPERTIES COMPILE_FLAGS "${cxx_flags}")
target_link_libraries(RobotiqHandPlugin_controlMsg ${catkin_LIBRARIES})
add_dependencies(RobotiqHandPlugin_controlMsg robotiq_s_model_articulated_msgs_gencpp)
add_dependencies(RobotiqHandPlugin_controlMsg robotiq_s_model_control_gencpp)

install(TARGETS RobotiqHandPlugin_controlMsg DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}/${PROJECT_NAME}/plugins/)


add_library(RobotiqHandPluginSingleHand src/RobotiqHandPluginSingleHand.cpp)
set_target_properties(RobotiqHandPluginSingleHand PROPERTIES LINK_FLAGS "${ld_flags}")
set_target_properties(RobotiqHandPluginSingleHand PROPERTIES COMPILE_FLAGS "${cxx_flags}")
target_link_libraries(RobotiqHandPluginSingleHand ${catkin_LIBRARIES})
add_dependencies(RobotiqHandPluginSingleHand robotiq_s_model_articulated_msgs_gencpp)
add_dependencies(RobotiqHandPluginSingleHand robotiq_s_model_control_gencpp)

install(TARGETS RobotiqHandPluginSingleHand DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}/${PROJECT_NAME}/plugins/)


add_library(RobotiqHandPluginSingleHand_controlMsg src/RobotiqHandPluginSingleHand_controlMsg.cpp)
set_target_properties(RobotiqHandPluginSingleHand_controlMsg PROPERTIES LINK_FLAGS "${ld_flags}")
set_target_properties(RobotiqHandPluginSingleHand_controlMsg PROPERTIES COMPILE_FLAGS "${cxx_flags}")
target_link_libraries(RobotiqHandPluginSingleHand_controlMsg ${catkin_LIBRARIES})
add_dependencies(RobotiqHandPluginSingleHand_controlMsg robotiq_s_model_control_gencpp)
add_dependencies(RobotiqHandPluginSingleHand_controlMsg robotiq_s_model_control_gencpp)

install(TARGETS RobotiqHandPluginSingleHand_controlMsg DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}/${PROJECT_NAME}/plugins/)
