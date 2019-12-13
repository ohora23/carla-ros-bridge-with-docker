
# ROS bridge for CARLA simulator (with modified Dockerfile)

This ROS package aims at providing a simple ROS bridge for CARLA simulator.
(forked from [carla-simulator/ros-bridge](https://github.com/carla-simulator/ros-bridge))

__Important Note:__
This documentation is for CARLA versions *newer* than 0.9.4.

![rviz setup](./docs/images/rviz_carla_default.png "rviz")


# Setup

## Create a workspace and clone the repository

    #setup folder structure
    mkdir ~/carla-ros-bridge
    cd ~/carla-ros-bridge
    git clone https://github.com/jjimin/carla-ros-bridge-with-docker.git

## Build a docker image with Dockerfile

See this [README.md](https://github.com/jjimin/carla-ros-bridge-with-docker/blob/master/docker/README.md) to build a docker image.


# Create and run a container

    #create a container that is capable to show gui display and mount a directory
    docker run -it --rm \
               -p 2000-2002:2000-2002 \
               --gpus all -e NVIDIA_VISIBLE_DEVICES=0 \
               -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY \
               -v ~/carla-ros-bridge/docker/data:/data \
               --name <your_container_name> \
               carla-ros-bridge:<your_tage_name> /bin/bash

# Start the ROS bridge

First run the simulator (see carla documentation: http://carla.readthedocs.io/en/latest/)

    ./CarlaUE4.sh -windowed -ResX=320 -ResY=240


Wait for the message:

    Waiting for the client to connect...

In another terminal, to start the ros bridge, set a environment.

#

When opening a new terminal, you should run the code below.

    export PYTHONPATH=$PYTHONPATH:/opt/carla/PythonAPI/carla/dist/carla-0.9.6-py2.7-linux-x86_64.egg
    source /opt/carla-ros-bridge/install/setup.bash
    
Check the installation is successfull by trying to import carla from python:

    python -c 'import carla;print("Success")'

You should see the Success message without any errors.

#

And start the ros bridge (choose one option):

    # Option 1: start the ros bridge
    roslaunch carla_ros_bridge carla_ros_bridge.launch

    # Option 2: start the ros bridge together with RVIZ
    roslaunch carla_ros_bridge carla_ros_bridge_with_rviz.launch

    # Option 3: start the ros bridge together with an example ego vehicle
    roslaunch carla_ros_bridge carla_ros_bridge_with_example_ego_vehicle.launch

There is a rviz configuration file in '.config/rviz'
    
    cp ~/.config/rviz/carla-ros-config.rviz ~/.rviz
    mv ~/.rviz/carla-ros-config.rviz ~/.rviz/default.rviz
    

    
