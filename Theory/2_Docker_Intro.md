**CONTAINERIZATION**

It is a lightweight form of virualization that allows to package and run the application along with the dependencies in an isolated environment called container.
__container__ is an isolated env to run an application.

__Advantages of containers:__
1) independent on OS
2) lightweight bcz they don't have complete OS it shares the Kernal
3) faster

![Virtualization vs Containerization](/Theory/images/vm-vs-containers.webp)

To implementing this process we need a software tool that is __DOCKER__.

**DOCKER**
Docker is a platform for developing, shipping and running applications inside containers.

__Containers__ you already learn at line __3__
inorder to create a container we need an executable package called Docker IMAGE which consists all the instructions,code,dependencies to run the containers. without images we can't create containers.
simply say IMAGES are read-only templates.

__Dockerfile__ is a Script containing a series of instructions to build an image.
for every line present in the dockerfile if forms a layer in the image.

For the references or future versions  we keep these images in a safe place called DOCKERHUB where we can push and pull the images with different versions

![](/Theory/images/dockerfile-2.png)

**DOCKER ARCHITECTURE**
![](/Theory/images/docker%20architecture.jpg)

__DOCKER CLIENT:__ is a command line interface where users can interact with docker deamon. It send commands to daemon through REST API
__DOCKER DAEMON:__ is like a heart of docker which listen the apis from client and process it and return the response back.
                    It manages the images,containers,volumes,networks etc.
__DOCKER REGISRTY:__ Is a cloud platform (Ex: Dockerhub, Amazon ECR, GCR,GHCR etc.) where we store our images.

To know more about Docker internals refer to the link [official docker documentation](https://docs.docker.com/get-started/overview/)

