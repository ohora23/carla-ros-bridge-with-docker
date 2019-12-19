# How to build this docker image
#### How to build the 'carla-ros-bridge-with-docker' with this Dockerfile (Dockerfile-carla-ros-bridge)
<hr/>
First, clone this repository. ([See this README.md](https://github.com/jjimin/carla-ros-bridge-with-docker))  

#
Second, you need to install a docker engine. If you don't install the docker, [please install it.](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

To use your GPU driver, install NVIDIA-docker too. You can figure out how to install in [here](https://github.com/NVIDIA/nvidia-docker.git).

After that, run the code below.
```
cd ~/carla-ros-bridge-with-docker/docker
docker build --tag carla-ros-bridge:<your_tage_name> -f Dockerfile-carla-ros-bridge ..
```
