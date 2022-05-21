# range_image_segment
A ROS package to perform `ground plane filter` for 3D lidar pointcloud.

# reference
* Fast segmentation of 3D point clouds: A paradigm on LiDAR data for autonomous vehicle applications, 2017.

## Requirement
* pcl 1.8 (https://github.com/PointCloudLibrary/pcl)
* ros kinetic or melodic

## Run
$ catkin_make
$ source ./devel/setup.bash
$ roslaunch ground_plane_fitting ground_plane_fitting.launch 