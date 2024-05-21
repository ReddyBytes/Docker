# 1) FROM directive to fetch the base image from Docker Hub
FROM python:3.8-slim-buster

# 2) RUN directive to update the package list and install dependencies
RUN apt-get update && \
    apt-get install -y curl && \
    rm -rf /var/lib/apt/lists/*

# 3) WORKDIR directive to set the working directory in the container
WORKDIR /app

# 4) COPY directive to copy the local files into the container
COPY . .

# 5) ADD directive to add a compressed file and extract it in the container
ADD requirements.txt .

# 6) ENV directive to set environment variables
ENV PORT=5000

# 7) EXPOSE directive to expose the application to a particular port
EXPOSE $PORT

# 8) ENTRYPOINT directive to run the specified command when the container starts
ENTRYPOINT ["python"]

# 9) CMD directive to set the default arguments for the entrypoint or act as the main command
CMD ["app.py"]

# 10) VOLUME directive to create a mount point with the container post to the Docker managed volumes
VOLUME ["/data"]


## DON'T RUN THIS DOCKERFILE THIS IS A SAMPLE FILE