FROM althack/ros2:foxy-dev 


ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
   && apt-get -y install --no-install-recommends \
   openjdk-11-jre \
   && pip3 install owlready2 \
   && pip install xacro \
   && apt update -y\
   && apt install ros-foxy-ros-ign -y\
   && apt-get autoremove -y \
   && apt-get clean -y \
   && rm -rf /var/lib/apt/lists/* 
ENV DEBIAN_FRONTEND=dialog


# nvidia-container-runtime
ENV NVIDIA_VISIBLE_DEVICES \
    ${NVIDIA_VISIBLE_DEVICES:-all}
ENV NVIDIA_DRIVER_CAPABILITIES \
    ${NVIDIA_DRIVER_CAPABILITIES:+$NVIDIA_DRIVER_CAPABILITIES,}graphics


# Set up auto-source of workspace for ros user
ARG WORKSPACE
RUN echo "if [ -f ${WORKSPACE}/install/setup.bash ]; then source ${WORKSPACE}/install/setup.bash; fi" >> /home/ros/.bashrc
# ENV GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:${WORKSPACE}/src/turtlebot3/turtlebot3_simulations/turtlebot3_gazebo/models:${WORKSPACE}/src/Pilot-URJC/pilot_urjc_bringup/worlds/models
# ENV TURTLEBOT3_MODEL=waffle
