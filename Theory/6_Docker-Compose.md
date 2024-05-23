
Before going into details lets understand how docker works .  
1) we have a pyton flask applicationand we need to dockerize it.
2) we create a dockerfile with required number of layers
3) we build an image
4) By using docker run command we create a docker container and 
5) we can access from the browser.  
   problem was solved than why we need docker compose ??  

# Docker compose  
Docker compose is multi container application. Don't worry i will explain in detail.  
lets say we are developind an Ecommerce application with can have [ login, logout, payments, cart, database, frontend ] etc  containers.  

when we use docker we need to run diff builds and containers which will take time and if the database container depends on login and logout then it is diff to use docker for building and running.  
so docker came up with __docker compose__   

we write a docker compose.yml file and by single command we can run all conatiners.  
  
    docker compose up

To bring down the containers use 
  
    docker compose down


you can find multiple docker compose.yml files and projects in this [repository](https://github.com/docker/awesome-compose) and try that by bulding that compose files.