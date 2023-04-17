### Pytorch-Blender Docker

This is my first attempt to create a container that can run in WSL2 with ubuntu 20.04.2 LTS to run Blender using X11.

## Build docker image

```bash
cd pytorch-blender/Docker
docker build -t snolot/blender_docker .

```

## Run docker image

```bash

 xhost +local:root

 docker run --rm --shm-size 12G --gpus all --net host \
 -e SHELL \
 -e DISPLAY=$DISPLAY \
 -e DOCKER=1 \
 -v="/etc/group:/etc/group:ro" \
 -v="/etc/passwd:/etc/passwd:ro" \
 -v="/etc/shadow:/etc/shadow:ro" \
 -v="/etc/sudoers.d:/etc/sudoers.d:ro" \
 -v="/tmp/.X11-unix:/tmp/.X11-unix:rw" 
 -v="/mnt/c/Documents and Settings/sno/Documents/ml/pytorch-blender:/pytorch-blender" -it snolot/blender_docker:latest

```


