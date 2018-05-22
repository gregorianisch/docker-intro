# Docker intro

## Simple container 

Commands should be runned in: `/simple_container` folder.

* Create image from Dockerfile, assign tag - `docker build -t react:app .`
* View all images - `docker images`
* Run container on port 3000 - `docker run -it -p 3000:3000 react:app`
* View all running containers - `docker ps`
* Stop container - `docker stop <container ID>`
* Remove container - `docker rm <container ID>`

> * Image - immutable file, snapshot, basis of container. Can contain layers of other images. "Class" in programming sense.
> * Container - runtime instance of a "class".
> * Tag - label applied to Docker image in repository to distinguish it from other images.

## Multi-containers

Commands should be runned in: `/multi_container` folder.

* Build multi-containers from docker-compose.yml file - `docker-compose build`
* Run multi-containers from docker-compose.yml file - `docker-compose up`
* View all running containers - `docker ps`
* Login to created MongoDB container through bash entrypoint - `docker exec -it <container ID> /bin/bash`
* Run mongo shell - `mongo`
* Show all databases - `show dbs`
* Switch to admin database - `use admin`
* Show database collections - `show collections`
* Look all objects of users collection - `db.users.find({})`
* View created volume - `docker volume ls`
* Inspect volume - `docker volume inspect <volume NAME>`

## Image to registry

Commands should be runned in: `/service_stack` folder.

* Login into Docker - `docker login`
* Tag image for repository - `docker tag <image NAME> gregorianisch/stagnation:service_stack`
* Push image to repository - `docker push gregorianisch/stagnation:service_stack`

## Service stack

Commands should be runned in: `/service_stack` folder.

* Enable swarm mode - `docker swarm init`
* Deploy service stack from docker-compose.yml file - `docker stack deploy -c docker-compose.yml service_example`
* View services list - `docker service ls`
* View tasks (replicas) of web service - `docker service ps service_example_web`
* Take stack down - `docker stack rm service_example`
* Leave swarm mode - `docker swarm leave --force`

> * Service - group of containers, which share same image:tag
> * Swarm - cluster of Docker engines running in swarm mode, which allows to deploy and orchestrate services collectively.
> * Stack - group of interrelated services that share dependencies, can be scaled together.

### Useful commands

* Run container in detached mode - `docker run -d -it -p 3000:3000 react:app`
* Remove all containers - `docker rm $(docker ps -a -q)`
* Remove all images - `docker rmi $(docker image ls -a -q)`
* Remove volumes - `docker volume rm $(docker volume ls -qf dangling=true)`
