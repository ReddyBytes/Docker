
- In general everthing(images, containers, volumes ,secreets etc ) will be storing in root volume (/var/lib/docker/) . 
- So, make sure that this root volume is not going to exceed 50% of storage although we have alarams,reminders set at 80-90%.

To know the root storage usage

    df -h 
- To avoid such cases we can use AWS EBS volumes and we can mount this volume in docker dir service.  


## Docker Socket 

- The Docker socket `/var/run/docker.sock` is a special file that allows communication with the Docker daemon. 
- It enables client programs to send commands to the Docker daemon, which manages Docker containers. 

if we implement this docker socket in container then we can use docker cli commands inside the container.
  
    docker run --rm -d --name app1 -v /var/run/docker.sock:/var/run/docker.sock --network none nginx


## portainer.io
this is a web UI tool where we can watch our docker containers, volumes, networks etc 

  
    docker create volume create portainerdata

    docker run -d -p 8000:8000 -p 9443:9443 --name portainer \
        --restart=always \
        -v /var/run/docker.sock:/var/run/docker.sock \
        -v portainer_data:/data \
        portainer/portainer-ce:2.11.1