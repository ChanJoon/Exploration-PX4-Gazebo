cmake_minimum_required(VERSION 2.8.3)
project(exploration_utils)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-std=c++14")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -w")

find_package(Eigen3 REQUIRED)
find_package(PCL 1.7 REQUIRED)
find_package(OpenCV REQUIRED)
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  tf
  visualization_msgs
  cv_bridge
  message_filters
  eigen_conversions
)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES exploration_utils
  CATKIN_DEPENDS roscpp std_msgs
  # DEPENDS system_lib
)

include_directories( 
  SYSTEM 
  include
  include/lkh_tsp_solver
  include/sop_solver
  ${catkin_INCLUDE_DIRS}
  ${Eigen3_INCLUDE_DIRS} 
  ${PCL_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

file(GLOB LKH_SRCS src/lkh_tsp_solver/*.c src/lkh_tsp_solver/*.cpp)
file(GLOB SOP_SRCS src/sop_solver/*.cpp) 

link_directories(${PCL_LIBRARY_DIRS})

add_library(exploration_utils 
  src/raycast/raycast.cpp
  src/transformer/transformer.cpp
  src/perception_utils/perception_utils.cpp
  src/system_info.cpp
  ${LKH_SRCS}
  ${SOP_SRCS}
)
target_link_libraries(exploration_utils
  ${catkin_LIBRARIES} 
  ${PCL_LIBRARIES}
)  