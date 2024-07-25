## Docker Swarm

Swarm in a Container Orchestration tool for small scale applications .
#### Drawbacks:
- auto scaling is not there
- small community
- TLS features are not supported
- Advanced storage and networking features are not supported
- RBAC missing


### How to setup Docker Swarm
__Step 1 :__ install docker swarm on your instance 
  
    docker swarm init

![](/Theory/images/Screenshot%202024-07-13%20at%2010.30.00 AM.png)

__Step 2 :__ copy those join commands for master and node and then use that commands in your other master nodes and worker nodes.

 below is the sample that how to join a worker node   

    root@ip-172-31-18-11:~# docker swarm join --token SWMTKN-1-317p6wmux4tnlcro04rk1g8id3r1gmzmp9qh1pzc6nwbhy4ldt-7w0t1zi9xqo7nxcdqp6ffdc1w 172.31.21.175:2377
    
    This node joined a swarm as a worker.

__Step 3 :__ To manage all the master and worker nodes through command line is difficult so use the below command in any node which is anothe container as a vizualizer.

Run this command in any one of the master node and access the UI with Public IP :8080 
   
     docker run -it -d -p 8080:8080 -v /var/run/docker.sock:/var/run/docker.sock dockersamples/visualizer

![](https://callistaenterprise.se/assets/blogg/docker/docker-in-swarm-mode-on-docker-in-docker/visualizer-8.png)

#### some docker swarm commands

to know the swarm status 
  
    docker info | grep -i swarm

to start service  

    docker service create --name app2 --replicas=2 --publish 8002:80 nginx

to list service 
  
    docker service ls

to remove service

    docker service rm <service name>
to scale the container
  
    docker service scale app2=3

to update the node 

    docker node update ip-<privaate ip in '-' format> --availability drain

    availability = drain,active,pause

    docker node update ip-172-10-27-13 --availability drain 

if you want to deploy ur containers only on master then use the below cammand
  
    docker service create --constraint=node.role==worker --name app3 --replicas=3 --publish 8000:81 nginx