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

## Run a container from a image (create the instance)
* **--name**: container name
* **-p**: port mapping
* **image-name**: base image
* **bash**: optional command to run at instance time

**$** docker **run** --name container-name -p 8888:8888 image-name bash
### Other options:
* **-i**: Keep STDIN open even if not attached
* **-t**: Allocate a pseudo-TTY
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
* **-u root** Run as root

**$** docker **exec** -it container-name command

## Remove image
**$** docker **rmi** image
