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


__Dockerfile commands:__

1) __FROM__ is used to fetch base image from local or dockerhub. 
        **FROM ubuntu:latest**
        **FROM python:3.2**

2) __RUN__ is used to execute the commands in new layer on top of the current image and commits the result.
        **RUN apt-get update -y**

3) __WORKDIR__ is used to set the working directory in the container where all copied files and run command need to execute 
        **WORKDIR /app**

4) __COPY__ is used to copy the local files into the container.
        **COPY . /app** # . is current directory and /app is the app present in the container

5) __ADD__ is used to add the local files to the container and has an extra feature like extracting compressed files.
        **ADD file.tar.gz**

6) __ENV__ is used to set the environment variables 
        **ENV PORT 5000**

7) __EXPOSE__ is used to expose the application to a particular port so that we can access the application from that port.
        **EXPOSE 5000**

8) __ENTRYPOINT__ is used to run the specified command when the container starts.it cannot be overridden
        **ENTRYPOINT ["python"]**

9) __CMD__ sets the default arguments for the entrypoint or acts as main command when entrypoint is not present.
        **CMD ["app.py"]**
        **CMD ["python","app.py"]**
10) __VOLUME__ it create a mount point with the container posth to the docker managed volumes so that the data will be persistent even container crashes
        **VOLUME [/path/to/file/in/container]**


These are the top dockerfile commands that we use daily to learn all docker file command [click](https://docs.docker.com/reference/dockerfile/)
see the sample docker [dockerfile](/code/Dockerfile)
