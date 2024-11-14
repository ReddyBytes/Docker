**CONTAINERIZATION**

It is a lightweight form of virualization that allows to package and run the application along with the dependencies in an isolated environment called container.
__container__ is an isolated env to run an application.

__Advantages of containers:__
1) independent on OS
2) lightweight bcz they don't have complete OS it shares the Kernaľ̌
3) faster

![Virtualization vs Containerization](/Theory/images/vm-vs-containers.webp)

To implementing this process we need a software tool that is __DOCKER__.  
Container Engine are like ContainerD, CRI-O 

## DOCKER  
Docker is a platform for developing, shipping and running applications inside containers. It seperates the application and infra so that we can test anywhere with all dependencies.

Main advantages:

1. __Portability :__ we can ship our application wherever we want

2. __Consistency :__ Irrespective of infra we will get the same output

3. __Isolation :__ seperation is there b/w infra and aplication

4. __Efficiency :__ we can work more efficient because there is no need of having the same dependencies in all systwms , dev, qa, prd. 

### Docker Image:  
- An image is an immutable, lightweight, standalone, executable package that includes everything needed to run a piece of software, including the code, runtime, libraries, environment variables, and config files.  
- It serves as a blueprint for creating containers. 
- Images are stored in a Docker registry and are composed of layers, which makes them efficient to transfer and version control. 
- IMAGES are read-only templates.  

- __"Lightweight"__ Containers share the machine's OS system kernel and therefore do not require an OS per application  
- __"Standalone"__ refers to something that exists or operates independently, without needing to connect to or be part of another entity or system.  

#### Dangling Images
- These are the images that does not have any interaction with tagged images.
- this images have no tag and name
for more info [check this page](https://www.howtogeek.com/devops/what-are-dangling-docker-images/)

#### Distroless Images
- These are the minimalistic images which doesn't have the shell (bash),packager managers etc.
- This images contains only the application and runtime dependencies.
### Containers  
- A Docker container is an instance of a Docker image that runs the actual application. 
-  It is an isolated environment where an application runs without affecting the rest of the system and without the system impacting the application
- container is a process to check that use  
      
      lsns -t pid
- containers are stateless means they do not store data between two sessions or on restarts


**DOCKER ARCHITECTURE** 

![](/Theory/images/docker%20architecture.jpg)

__DOCKER CLIENT:__  
 - Is a command line interface where users can interact with docker deamon. It send commands to daemon through REST API  

__DOCKER DAEMON:__   
- Is like a heart of docker which listen the apis from client and process it and return the response back.
- It manages the images,containers,volumes,networks etc.  

__DOCKER REGISRTY:__  
 - Is a cloud platform (Ex: Dockerhub, Amazon ECR, GCR,GHCR etc.) where we store our images.

To know more about Docker internals refer to the link [official docker documentation](https://docs.docker.com/get-started/overview/)

---
---
---

### Snapshot : 

 A snapshot refers to a point-in-time capture of a container's state, including its file system, processes, and configuration settings.   

### Difference between Images and Snapshot : 

| Aspect | Docker Image | Snapshot |
|--------|--------------|----------|
| Definition | A Docker image is a read-only template that contains instructions for creating a Docker container. It acts as a blueprint of the libraries and dependencies required inside a container for an application to run. | A snapshot is a point-in-time copy of a container's state, including its file system, processes, and configuration settings. It can be used to create a new image. |
| Purpose | Used to create containers. It provides a consistent environment for applications to run. | Used to capture the current state of a container for backup, migration, or version control purposes. |
| Creation | Created from a Dockerfile or imported from a tarball. | Created from a running container using the `docker commit` command. |
| Storage | Stored in a Docker registry for sharing and reuse. | Not explicitly stored; instead, represents a state that can be recreated from an image. |
| Mutability | Immutable; cannot be changed once created. Changes result in a new image. | Mutable; reflects the current state of a container, which can evolve over time. |
| Use Case | Basis for deploying applications consistently across different environments. | Useful for preserving the state of a container for later restoration or analysis. 
|  Multiple  |  By using images we can create multiple containers  |  By using snapshots we can create multiple instances of containers and multiple VM's also 
