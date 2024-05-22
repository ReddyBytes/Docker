
lets try to understand volumes witha an example .
lets say we created an nginx container and it stores the user data and all activities in a log file .


__problem 1)__ if the container crashes we lost all this data because of container are  ephimeral(less life span) in nature .

__problem 2)__ we have 2 containers named frontend and backend and there is connection between them .if any one container is lost then the other is lost the previous data to server to the users which may cause sidcomfort to the usrs.

 to overcome this types of data loss when the container losts docker provides 2 solutions 

 # 1) Bind Mounts:

 ----->  we can store the details of container and logs of particular app in container with the a directory of the docker host.

 ----->  These are persistent(permanent).

 ------> we can share these mounts to multiple containers.

 <span style="color:green;">docker run -v /host/directory:/container/directory my_image</span>

 host location : location of the file in container


 # 2) Volumes:

 ----> similar to mounts but this does not dependent on the file system of the host it creates a space for the volume ans stores the container data.

 ----> Managed by Docker.

 ----> Data persists independently of the container’s life cycle.

 ----> Can be shared and reused among multiple containers.

 ----> Can be configured to have read-only access or to be writable by the container.

 ----> we can create volumes not only in Host we can use another ec2 instance or s3 or any cloud storage also.

 <span style="color:green;">docker run -v my_volume:/path/in/container my_image</span>

 ![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQO_02QnEX4Iusmdk7e8DRhmOjdCKBgU3P1xIduXPW7XQ&s)

better go with volumes than mounts 

Creating Volumes
--
Create a volume:
  
    docker volume create VOLUME_NAME
This command creates a new volume with the specified name.

- Listing Volumes

List all volumes:
  
    docker volume ls
Lists all volumes available on the system.

- Inspecting Volumes

Inspect a volume:
  
    docker volume inspect VOLUME_NAME
Provides detailed information about the specified volume, such as its location on the host filesystem.

- Removing Volumes

Remove a volume:
  
    docker volume rm VOLUME_NAME
Removes the specified volume. Note that you cannot remove a volume that is being used by a container.

- Pruning Volumes

Prune unused volumes:
  
    docker volume prune
Removes all local volumes not used by at least one container. Be cautious with this command, as it can delete more than you intend if you have many volumes.

Create a container with a volume:
  
    docker run -v VOLUME_NAME:/path/in/container IMAGE
Runs a container with a volume attached. Data written to /path/in/container inside the container will be stored in VOLUME_NAME.

Mount a volume into a running container:
  
    docker run -d --name CONTAINER_NAME -v VOLUME_NAME:/path/in/container IMAGE