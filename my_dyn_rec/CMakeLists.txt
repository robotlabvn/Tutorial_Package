cmake_minimum_required(VERSION 2.8.3)
project(my_dyn_rec)

find_package(catkin REQUIRED COMPONENTS
  dynamic_reconfigure
  roscpp
  rospy
)

generate_dynamic_reconfigure_options(
  cfg/MyParams.cfg
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(my_node src/my_node.cpp)

add_dependencies(my_node ${PROJECT_NAME}_gencfg)

target_link_libraries(my_node
  ${catkin_LIBRARIES}
)
