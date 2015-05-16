# docker-nuke
This is a Dockerfile that builds a container from CentOS 6.6 with working X Window System, NVIDIA Drivers and of course The Foundry's Nuke.
Tested on Fedora 19 and CentOS 6.6 as host machines.

*NVIDIA Driver running inside the Container _must_ match the Hosts loaded driver module.*

### to build
    wget http://raw.githubusercontent.com/remisdemis/docker-nuke/master/Dockerfile

    Then change the ENV's to whatever you need to install.
    Also you need to specify where your installer of Nuke is located.

    docker build -t nuke .

### to run
    docker run -it -v /tmp/.X11-unix:/tmp/.X11-unix \
        -e DISPLAY=unix$DISPLAY
        -v /dev/nvidia0:/dev/nvidia0 \
        -v /dev/nvidiactl:/dev/nvidiactl \
        --privileged nuke

