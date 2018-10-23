# Setting up extra tools needed to make the FLA codebase work on the Xavier

Assuming that you have already [installed ROS](http://wiki.ros.org/melodic/Installation/Ubuntu) using the ROS-desktop variant, 
the following can help you install all the required software packages.

### CUDA SGM

1. Install [PCL_ROS](http://wiki.ros.org/pcl) and Image_View
```
sudo apt-get update
sudo apt install ros-melodic-pcl-ros ros-melodic-image-view
```

2. Build CUDA ROS SGM Package
```
cd /../cuda_sgm_ros
catkin bt
```
Apart from some deprecated syntax warnings, it should build fine.

3. Download test data

```
a) Get the original bag file from this folder: 
   https://drive.google.com/open?id=1Qplh9fYt10t5H1p_adJkjhk3T7CjE2Xw
b) Also download the calibration file 
   file: fisheye_stereo_rectify.yml 
```

4. Move the calibration file to the .ros folder
```
mv fisheye_stereo_rectify.yml ~/.ros/
```

5. Re-map image topics and launch stereo_gpu.launch
```
roslaunch cuda_sgm_ros stereo_gpu.launch
```

6. Visualize
```
# Disparity View
rosrun image_view disparity_view image:=/stereo_gpu/disparity
# Disparity Image
rqt_image_view
```
