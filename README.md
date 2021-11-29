This repository contains two docker files that build from ubuntu 20.04 with cuda 11.4.2 and cudnn8.
The file Dockerfile_ROSnoetic installs the ROS noetic distribution.
The file Dockerfile_ROS2 installs ROS2 galactic distribution.

In this readme, you can find some basic instructions for building and using these images.



# Build the Dockerfile

## To build from directory

Download the dockerfile ** to a directory different from the HOME directory**, and from that directory, run the following comand: 

```bash
docker build -t nvidia_noetic .
```



## To build from file

To run a Dockerfile with filename Dockerfile_ROS2, and giving the docker container the name nvidia_ros2:

```bash
docker build -t nvidia_ros2 -f Dockerfile_ROS2 .
```

 
# Start a terminal

Run dockerfile with graphical interface

```bash
docker run -it --net=host --gpus all \
    --env="NVIDIA_DRIVER_CAPABILITIES=all" \
    --env="DISPLAY" \
    --env="QT_X11_NO_MITSHM=1" \
    --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
    nvidia_noetic \
    bash
```

# List docker images

```bash
docker images
```