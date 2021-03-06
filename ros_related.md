# Extra ROS Related Tools

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

Some benchmarks on the **CUDA Semi Global Matching** ROS Node:
![CUDA_Benchmark](/figs/cuda_sgm.png)

### Creating an isolated ROS Workspace for Python 3.5 Deep Learning

1. Create a workspace
```
cd ~
mkdir ros_py35
cd ros_py35
```

2. Unset existing ROS workspaces if you have any
```
vim ~/.bashrc
```

3. Get Python3 helpers
```
sudo pip3 install rosdep
sudo pip3 install rosinstall_generator
sudo pip3 install wstool
sudo pip3 install rosinstall
```

4. Configure your catkin workspace
```
mkdir src
catkin config --init
catkin config -DCMAKE_BUILD_TYPE=Release
```




















