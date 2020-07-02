# docker-notes
Docker command lists for basic/common usage

## Concepts:
* **images**: saved state of the container
* **container**: instance of a image
* **dockerfile**: file that describes all the steps needed to build a docker image

## List running containers
**$** docker **ps**

## List all containers
**$** docker **ps** -a

## Stop container
**$** docker **stop** container

## Remove container
**$** docker **rm** container

## Get an image from Docker Hub
**$** docker **pull** image-name

## List available images
**$** docker **images**

## Create a container from a image (create the instance)
**$** docker **create** --name container-name image-name

### Pratical example:
**$** nvidia-docker create -i -t -v <external-folder>:/workspace --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -e DISPLAY=$DISPLAY --device=/dev/video0:/dev/video0 --privileged -v /tmp/.X11-unix:/tmp/.X11-unix:rw --name <new-container-name> <image-name:tag>

## Run a container from a image (create instance and run)
* **--name**: container name
* **-p**: port mapping
* **image-name**: base image
* **bash**: optional command to run at instance time

**$** docker **run** --name container-name -p 8888:8888 image-name bash
### Other options:
* **-i**: Keep STDIN open even if not attached
* **-t**: Allocate a pseudo-TTY
* **-d**: Detached mode: run command in the background
* **-e**: Set environment variables (ex.: DISPLAY=$DISPLAY)
* **-u**: Username or UID (format: <name|uid>[:<group|gid>]) (ex.: $(id -u):$(id -g))
* **-v**: Bind mount a volume (ex.: ~/projects:/projects)
* **--network**: Connect a container to a network (ex.: host)
* **--privileged**: Give extended privileges to this container

## Starts a container (make it ready for usage)
**$** docker **start** container

## Execute a command from a existing image
* **-i**: Keep STDIN open even if not attached
* **-t**: Allocate a pseudo-TTY
* **-d**: Detached mode: run command in the background
* **-u root** Run as root

**$** docker **exec** -it container-name command

## Remove image
**$** docker **rmi** image

## Remove dangling images
**$** docker images **purge**

## List dangling images
**$** docker images **-f dangling=true**

## Purge all dangling images, containers, volumes, and networks
**$** docker **system prune**

## Remove any stopped containers and all unused images (not just dangling images)
**$** docker **system prune -a**

## Issues and Solutions
If the following error appear trying to open a app with ui interface

_No protocol specified
QXcbConnection: Could not connect to display :0
Aborted (core dumped)_

execute this command outside docker:

**$** xhost +local:docker
