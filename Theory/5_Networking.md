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


Multi-Host Networking  
--
Create a Custom Network: Creates a custom network for inter-container communication.
  
    docker network create --driver bridge <network_name>
Connect Containers to a Network: Connects containers to a specified network.
  
    docker network connect <network_name> <container_id_or_name>
Disconnect Containers from a Network: Disconnects containers from a specified network.
  
    docker network disconnect <network_name> <container_id_or_name>
