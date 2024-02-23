# Display ANYmal Lidar

## Overview

A simple repo for displaying the ANYmal robot with a point cloud generated from a ply file.

<img src="https://raw.githubusercontent.com/ddebenedittis/media/main/display_anymal_lidar/img/cover.png">

## Installation with Docker

Install [Docker Community Edition](https://docs.docker.com/engine/install/ubuntu/) (ex Docker Engine) and [Manage Docker as a non-root user](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user).

Install NVIDIA proprietary drivers if the NVIDIA graphics card should be used.

Install [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#setting-up-nvidia-container-toolkit) (nvidia-docker2) for NVIDIA support in the container. \
If you do not want to use NVIDIA, edit the Docker image to remove the NVIDIA section and the `run.bash` script, removing the `--gpus all` flag in the docker run command.

## Usage

Build the docker image (`-r` to rebuild the underlying images) :
```shell
./build.bash [-r]
```

Run the container:
```shell
./run.bash
```

Build the ROS workspace:
```shell
colcon build --symlink-install --cmake-args -DCMAKE_BUILD_TYPE=Release -DCMAKE_EXPORT_COMPILE_COMMANDS=ON && source install/setup.bash
```

Display the ANYmal robot and the lidar map with
```
ros2 launch anymal_c_simple_description anymal_lidar.launch.py [ply_file:=./plot.ply]
```
The map file can be changed with the optional argument `ply_file`.
