# DOCKER COMMANDS

to install the docker using shell script
  
    curl https://get.docker.com | bash

install from [official website](https://docs.docker.com/engine/install/ubuntu/)
  
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh get-docker.sh
    Executing docker install script, commit: 7cae5f8b0decc17d6571f9f52eb840fbc13b2737
    <...>

Gives docker version  
    
      •	docker --version  
  
     •	docker -v

Gives details about how many containers running/paused/stopped, images etc. 

    •	docker info

Gives the list of docker commands we can run
    
    •	docker --help

Get the help details about the specified command

    •	docker command --help
    example: docker get info --help

login to docker hub - https://hub.docker.com/
It will ask for username and password

    •	docker login

  
logout from docker hub

    •	docker logout

  
    
Images:
--
 Pull an Image: Downloads an image from a registry.
  
    docker pull <image_name>:<tag>

- Pushing Images

Tag an Image: Adds a tag to an image, preparing it for pushing.
  
    docker tag <source_image> <new_tag>
Push an Image: Uploads an image to a registry.
  
    docker push <image_name>:<tag>
- Listing Images

List Local Images: Shows all images available locally.
  
    docker images
List Remote Images: Lists images available in a remote registry.
  
    docker manifest inspect <remote_registry>/<image_name>:<tag>
- Building Images

Build an Image: Constructs an image from a Dockerfile.
  
    docker build -t <image_name>:<tag> .
    docker build -t <image_name>:<tag> -f <dockerfile name> . --no-cache
Build with BuildKit: Uses BuildKit backend for building images.
  
    DOCKER_BUILDKIT=1 docker build -t <image_name>:<tag>.
- Inspecting Images
 Inspect an Image: Provides detailed information about an image.
  
    docker image inspect <image_name>:<tag>
- Cleaning Up Images

Remove an Image: Deletes an unused image.
  
    docker rmi <image_id>  
    

Remove All Unused Images: Removes all dangling and unreferenced images.
  
    docker image prune
Force Remove an Image: Forces removal of an image even if it's being used by stopped containers.
  
    docker rmi -f <image_id>
- Exporting and Importing Images

Export an Image: Exports an image to a tar archive.
  
    docker save <image_name>:<tag> > <filename>.tar
Import an Image: Imports an image from a tar archive.
  
    cat <filename>.tar | docker load
- Setting Image Properties

Set Image Name and Tag: Sets the name and tag of an image.
  
    docker image rename <old_image_name>:<old_tag> <new_image_name>:<new_tag>
- Advanced Image Operations

Analyze an Image: Analyzes an image to determine its size and layers.
  
    docker image analyze <image_name>:<tag>

History of an Image: Shows the history of an image.
  
    docker image history <image_name>:<tag>
     • docker exec -it <container_name> <command>
 Executes a command in a running container.  
 And used to go into the container

 
 Logs:
 --
 Shows logs for a container.
  
    docker logs <container_id_or_name>
Follow Logs: Streams logs in real-time.
  
    docker logs -f <container_id_or_name>

`apt install jq` is used to view the logs in json format 
  
    cd /var/lib/docker/container/<container_id_or_name> 
    cat <logfile.log> | jq

Port Mapping  
==
Port Forwarding: Maps a network port to a container port.
  
    docker run -p <host_port>:<container_port> <image_name>:<tag>
Publish All Ports: Publishes all exposed ports to random high-numbered ports.
  
    docker run -P <image_name>:<tag>
Link Containers: Links two containers together.
  
    docker link <container_id_or_name_1> <container_id_or_name_2>

Resource Allocation  
===
Allocate Resources: Limits resource usage for a container.
  
    docker run --cpus=".50" --memory="100M" <image_name>:<tag>
CPU Priority: Sets CPU priority for a container.
  
    docker run --cpu-shares=512 <image_name>:<tag>
Advanced Configuration
Environment Variables: Passes environment variables to a container.
  
    docker run -e VARNAME=value <image_name>:<tag>
Mount Volumes: Mounts a volume to a container.
  
    docker run -v /host/path:/container/path <image_name>:<tag>
Entrypoint and Command: Overrides the default entrypoint and command.
  
    docker run --entrypoint=/usr/bin/some-command <image_name>:<tag>

Copy Files/Folders Between a Container and the Host
--

Copy files/folders from the host to the container:
  
    docker cp <host-path> <container-id-or-name>:<container-path>
Copy files/folders from the container to the host:
  
    docker cp <container-id-or-name>:<container-path> <host-path>

 Containers
 --
Run a container from the latest Ubuntu image without publishing ports:
  
    docker run -d --name my_container nginx

to delete the container automatically from the background also when we stop the container  
  
    docker run --rm --name my_container nginx
Run a container from the latest Nginx image, bind mount a volume, and publish port 80:
  
    docker run -d -v /path/to/local/dir:/usr/share/nginx/html -p 8080:80 --name nginx_container nginx
Attach to a Running Container  
To attach to a running container's standard input, output, and error streams, use the docker attach command.

  
    docker attach CONTAINER_ID_OR_NAME
- Inspecting Containers

List All Containers
To list all containers (running and stopped), 

  
    docker ps [-a|--all]
-a or --all: Show all containers (default shows only running).  
-q: Only show numeric IDs.

Inspect a Container
To get detailed information about a container, use the docker inspect command.

  
    docker inspect CONTAINER_ID_OR_NAME
- Stopping and Removing Containers

Stop a Container
To stop a running container, use the docker stop command.

  
    docker stop CONTAINER_ID_OR_NAME

    docker stop $(docker ps -aq)

Remove a Container
To remove one or more containers, use the docker rm command.

  
    docker rm CONTAINER_ID_OR_NAME
To remove a stopped container, simply use docker rm.  
To remove a running container, use docker rm with the -f  
To remove all stopped containers, use the docker container prune command.

  
    docker container prune

Restart a Container

To restart a container, you can use the docker restart command followed by the container ID or name. This command stops and then starts the container again.

  
    docker restart CONTAINER_ID_OR_NAME
Example
Suppose you have a container named my_web_app that you want to restart. You would execute:

  
    docker restart my_web_app
- Pause/Unpause a Container

Pausing a container suspends its execution, and unpausing resumes it. This can be useful for temporarily halting a container without stopping it entirely.

Pause a Container
  
    docker pause CONTAINER_ID_OR_NAME
Unpause a Container
  
    docker unpause CONTAINER_ID_OR_NAME
Example
To pause a container named my_database, you would use:

docker pause my_database
And to resume it, you would use:

  
    docker unpause my_database
- Viewing Logs

The docker logs command allows you to view the logs generated by a container. This can be particularly useful for debugging purposes.

  
    docker logs CONTAINER_ID_OR_NAME
Example
To view the logs for a container named my_application, you would execute:

  
    docker logs my_application
Additionally, you can follow the logs in real-time, similar to tail -f, by appending the -f flag:

  
    docker logs -f CONTAINER_ID_OR_NAME

To view the processcess present in the container, run the following command.
  
    docker exec container-id ps -eaf 


to view the same processess running in the host  we can see diff Process id for same container bcz of namespaces. 

    ps -ef

    pd -eaf | grep process-name 

    lsns   # to list the namespaces
    
    lsns -t pid    # to list the pid

    watch lsns -t pid   # to watch the pids 


script to run multiple containers
  
    for I in {1..10}; do
    > docker run -d nginx
    > done

to set alias for docker commands use 
  
    nano .bashrc

    source .bashrc


