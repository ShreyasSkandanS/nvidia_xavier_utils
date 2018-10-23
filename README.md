# NVIDIA Jetson AGX Xavier Utilities

Scripts and tips for working with the NVIDIA Jetson AGX Xavier. A blog-post of my initial reactions to the Jetson Xavier Development Kit can be found [here](https://shreyasskandan.github.io/posts/jetsonxavier-initialthoughts/)

### Setting Power Modes - 10W, 15W and 30W

For a detailed view of power mode configuation, look at the nvpmodel.conf figure file:
```
cat /etc/nvpmodel.conf
```
To check your system's current settings:
```
nvpmodel -q --verbose
```

If you're interested in enabling or switching between specific modes,

1. 10W Operating Mode
```
nvpmodel -m 1
```

2. 15W Operating Mode
```
# 4 CPU 
nvpmodel -m 2
```

3. 30W Operating Mode
```
# all CPU
nvpmodel -m 3
# 6 CPU
nvpmodel -m 4
# 4 CPU
nvpmodel -m 5
# 2 CPU 
nvpmodel -m  6
```



### Installing individual packages from Jetpack 4.1

In your terminal set a variable for the parent data folder:
```
jp_root="https://developer.download.nvidia.com/devzone/devcenter/mobile/jetpack_l4t/4.1/walpdzz/JetPackL4T_4.1_b5"
```
1. CUDA 10.0
```
wget $jp_root/cuda-repo-l4t-10-0-local-10.0.117_1.0-1_arm64.deb
```

2. CuDNN 7.3
```
wget $jp_root/libcudnn7_7.3.0.21-1+cuda10.0_arm64.deb
wget $jp_root/libcudnn7-dev_7.3.0.21-1+cuda10.0_arm64.deb
wget $jp_root/libcudnn7-doc_7.3.0.21-1+cuda10.0_arm64.deb
```

3. OpenCV 3.3.1
```
wget $jp_root/libopencv_3.3.1_arm64.deb
wget $jp_root/libopencv-dev_3.3.1_arm64.deb
wget $jp_root/libopencv-python_3.3.1_arm64.deb
wget $jp_root/libopencv-samples_3.3.1_arm64.deb
```

4. TensorRT 5.0
```
wget $jp_root/tensorrt_5.0.0.8-1+cuda10.0_arm64.deb
```

5. Other packages
```
wget $jp_root/Jetson_Linux_R31.0.2_aarch64.tbz2
wget $jp_root/libgie-dev_5.0.0-1+cuda10.0_arm64.deb
wget $jp_root/libnvinfer5_5.0.0-1+cuda10.0_arm64.deb
wget $jp_root/libnvinfer-dev_5.0.0-1+cuda10.0_arm64.deb
wget $jp_root/libnvinfer-samples_5.0.0-1+cuda10.0_arm64.deb
wget $jp_root/libvisionworks-repo_1.6.0.500n_arm64.deb
wget $jp_root/libvisionworks-sfm-repo_0.90.3_arm64.deb
wget $jp_root/libvisionworks-tracking-repo_0.88.2_arm64.deb
wget $jp_root/Tegra_Linux_Sample-Root-Filesystem_R31.0.2_aarch64.tbz2
wget $jp_root/Tegra_Multimedia_API_R31.0.2_aarch64.tbz2
```
Once downloaded, you can install the .deb files as usual (click [here](https://unix.stackexchange.com/questions/159094/how-to-install-a-deb-file-by-dpkg-i-or-by-apt) if you are not familiar).

### Setup SSH

It should come with this pre-installed but in case it isn't:
```
sudo apt install openssh-client
sudo apt install openssh-server
```
