cmake_minimum_required(VERSION 2.8.3)
project(ground_plane_fitting)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  pcl_ros
  pcl_conversions
  dynamic_reconfigure
)


## Generate dynamic reconfigure parameters in the 'cfg' folder
generate_dynamic_reconfigure_options(
  cfg/ground_plane_fitting.cfg
)

catkin_package(CATKIN_DEPENDS
	sensor_msgs
)


###########
## Build ##
###########

include_directories(
  ${catkin_INCLUDE_DIRS}
)

find_package(Eigen3 REQUIRED)

SET(CMAKE_CXX_FLAGS "-std=c++11 -O2 -g -Wall ${CMAKE_CXX_FLAGS}")

link_directories(${PCL_LIBRARY_DIRS})

#Ground Plane Fitter
find_package(PCL 1.8 REQUIRED)
add_definitions(${PCL_DEFINITIONS})

add_executable(groundplanfit 
	src/groundplanfit.cpp
)

target_include_directories(groundplanfit PRIVATE
	${PCL_INCLUDE_DIRS}
)

target_link_libraries(groundplanfit
	${catkin_LIBRARIES}
	${PCL_LIBRARIES}
)