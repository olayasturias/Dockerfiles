FROM nvidia/cuda:11.4.2-cudnn8-devel-ubuntu20.04

# Minimal setup
RUN apt-get update 
RUN apt-get install -y locales lsb-release

ARG DEBIAN_FRONTEND=noninteractive
RUN dpkg-reconfigure locales

# Install ROS Noetic
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
RUN apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
RUN apt-get update \
 && apt-get install -y --no-install-recommends ros-noetic-desktop-full
RUN apt-get install -y --no-install-recommends python3-rosdep
RUN rosdep init \
 && rosdep fix-permissions \
 && rosdep update
RUN echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc

# Install Git
RUN apt-get update && apt-get install -y git

# Create a Catkin workspace 
RUN apt-get install python3-catkin-tools python3-osrf-pycommon
# Change the default shell to Bash
SHELL [ "/bin/bash" , "-c" ]

RUN source /opt/ros/noetic/setup.bash \
 && mkdir -p /remaro_ws/src \
 && cd /remaro_ws/src \
 && catkin_init_workspace  \
 && cd .. \
 && catkin build