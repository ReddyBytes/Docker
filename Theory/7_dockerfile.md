### Dockerfile 
 Is a Script containing a series of instructions to build an image.
for every line present in the dockerfile if forms a layer in the image.

For the references or future versions  we keep these images in a safe place called __DOCKERHUB__ where we can push and pull the images with different versions

![](/Theory/images/dockerfile-2.png)

__Dockerfile commands:__

1) __FROM__ is used to fetch base image from local or dockerhub.  
    
        FROM ubuntu:latest
        FROM python:3.2

2) __RUN__ is used to execute the commands in new layer on top of the current image and commits the result.
        
        RUN apt-get update -y

3) __WORKDIR__ is used to set the working directory in the container where all copied files and run command need to execute 
        
        WORKDIR /app

4) __COPY__ is used to copy the local files into the container.
        
        COPY . /app  
    . is current directory and /app is the app present in the container

5) __ADD__ is used to add the local files to the container and has an extra feature like extracting compressed files.
        
        ADD file.tar.gz

6) __ENV__ is used to set the environment variables  
this env variables can pass while running the containers

        
        ENV PORT 5000

7) __EXPOSE__ is used to expose the application to a particular port so that we can access the application from that port.
       
       
       EXPOSE 5000

8) __ENTRYPOINT__ is used to run the specified command when the container starts.it cannot be overridden
        
        ENTRYPOINT ["python"]

9)  __CMD__ sets the default arguments for the entrypoint or acts as main command when entrypoint is not present.
        
        CMD ["app.py"]
        CMD ["python","app.py"]
10) __VOLUME__ it create a mount point with the container posth to the docker managed volumes so that the data will be persistent even container crashes
        
        VOLUME [/path/to/file/in/container]

11) __LABEL__ is used to give the key value pair 
  
    
      
        LABEL key="test_image"

12) __ARG__ are the build args  
this args can be pass while building the images
  
    
      
        ARG P_VERSION=3.10

        docker build -t <imagename with tag> --build-arg P_VERSION=3.10 -f <dockerfile> .

These are the top dockerfile commands that we use daily to learn all docker file command [click](https://docs.docker.com/reference/dockerfile/)
see the sample docker [dockerfile](/code/Dockerfile)
