
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

__How to create volumes ??__

1) <span style="color:orange;">docker volume create "volume name"</span>
   
   it means that a logical partion is created in in the host (ec2 instance) with name ex: volume = <span style="color:orange;">boss</span>

2) <span style="color:orange;">docker volume ls</span>
    
    it showa the entire volumes present in the host

3) <span style="color:orange;">docker volume inspect boss</span>
    
    it shows entore data of particular volure details date,location etc.

4) <span style="color:orange;">docker volume ls</span>
    
    it deletes the volume name called boss

5) <span style="color:orange;">docker run -d -v boss:/app ngnix</span>
    
    nginx is the image, /app is the folder present in the container we are mapping this container folder to the volume present in the host

6) <span style="color:orange;">docker run -d --mount source=boss,target=/app ngnix</span>  
   we use in mount format also for easy understanding.  

7) <span style="color:orange;">docker volume rm <volume_name> </span>  
   Remove a Volume: Deletes a volume.

8) <span style="color:orange;">docker volume prune<volume_name> </span>  
   Prune Volumes: Removes all unused volumes.
   
9)  <span style="color:orange;">docker volume rm <volume_name> </span>  
    
10) <span style="color:orange;">docker volume rm <volume_name> </span>  

11) 

     

 
