# Networking  

Basically Networking allows to communicate between 2 containers and  host system.  

Generally how container 1 talks with container 2 is by using differen networks.  
## 1) Bridge Networking  
There is a __etho__ network is created by default when a host or container is created and to communicate betweeen 2 containers a __virtual etho network (veth)__ called __dockerO__ is  created by default we called this as __Bridge Networking__ is a default network created by docker.   

![](https://miro.medium.com/v2/resize:fit:1060/0*cMUND9w1bO1o5sPe.png)  

without BridgeNetwork there is no connection or communication is possible b/w containers.  

## 2) Host Networking.  
 In this type of networking both host ans container share the same networking which is unsecure.  
 ![](https://media.geeksforgeeks.org/wp-content/uploads/20240215171346/image-189.webp)  
 here we can see both are sharing the same networking.  
 Hackers can access easily our container if he access the host because same are sharing the same networking.

 ## 3) Overlay Networking.  
A virtual or Logical network created on the top of the physical server.  
By using this networking  containers can talk to each other from multiple hosts means multiple ec2 instances.   
This type of networking is mostly used in te Docker Swarm and K8s.  


![](https://miro.medium.com/v2/resize:fit:904/0*-Si1piI584OyYZuA)  



__we can create custom Bridge networks so that containers can talk with host  
so that the seperation is possible between diff container like ( login,logout, payments are 3 containers) for login and logout can has same Host networking and for Payments we can create custom bridge networking__  

Practice the commands by creating custom networks try that 2 containers ate talk to each other or not try with custom network container and host network container are talking or not etc.

For information about networking you can see [here ](https://docs.docker.com/network/)   

[Youtube video on networking](https://www.youtube.com/watch?v=xrUGEoUpa3s&list=PLdpzxOOAlwvLjb0vTD9BXLOwwLD_GWCmC&index=6)
## Networking Basic commands
List Networks: Displays all networks.
  
    docker network ls
Inspect a Network: Shows detailed information about a network.
  
    docker network inspect <network_name>
Create a Network: Creates a new network.
  
    docker network create <network_name>
Connect a Container to a Network: Connects a container to a network.



    docker network connect <network_name> <container_name>
Disconnect a Container from a Network: Disconnects a container from a network.
  
    docker network disconnect <network_name> <container_name>

Delete a Network
  
    docker network rm NETWORK  

Multi-Host Networking  
--
Create a Custom Network: Creates a custom network for inter-container communication.
  
    docker network create --driver bridge <network_name>
Connect Containers to a Network: Connects containers to a specified network.
  
    docker network connect <network_name> <container_id_or_name>
Disconnect Containers from a Network: Disconnects containers from a specified network.
  
    docker network disconnect <network_name> <container_id_or_name>
