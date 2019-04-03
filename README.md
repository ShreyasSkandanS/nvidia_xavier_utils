# NVIDIA Jetson AGX Xavier Utilities

Scripts and tips for working with the NVIDIA Jetson AGX Xavier. A blog-post of my initial reactions to the Jetson Xavier Development Kit can be found [here](https://shreyasskandan.github.io/posts/jetsonxavier-initialthoughts/)

![Xavier](https://shreyasskandan.github.io/images/IMG_3352.jpg)

1. [Basic Installation and Setup](basic_setup.md)
  * Using power modes 10W, 15W and 30W
  * Installing individual packages (from JetPack 4.1)
  * Setting up SSH
2. [ROS Related Tips](ros_related.md)
  * Building CUDA_SGM_ROS and benchmarks
  * Creating isolated Python3.5 ROS workspace
3. [PyTorch Tips](pytorch_setup.md)
  * Installing PyTorch from pip wheel
  * Testing inference of ss_segmentation based on ERFNet
4. [Decasing Developer Kit](decasing_xavier.md)
  * Removing the cooling enclosure
  * Detaching module from heat sink and enclosure
  * Weight of bare module and carrier board
