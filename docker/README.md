# How to build this docker image
#### How to build the 'carla-ros-bridge-with-docker' with this Dockerfile (Dockerfile-carla-ros-bridge)
<hr/>
First, clone this repository. ([See this README.md](https://github.com/jjimin/carla-ros-bridge-with-docker))  

#
And, run the code below.
(If you don't install the docker, [please install it.](https://docs.docker.com/install/linux/docker-ce/ubuntu/))
```
cd ~/carla-ros-bridge/ros-bridge/docker
docker build -t carla-ros-bridge:jimin-custom -f Dockerfile-carla-ros-bridge ..
```
