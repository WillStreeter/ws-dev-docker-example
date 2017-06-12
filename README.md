# ws-dev-docker-example
#### A configuraton of a Docker eco-system as a FullStack integrated development environment


## Architecture:
This repository is part of a larger effort to expound on the strategies and approaches delineated in the article
[Practical Web Development and Architecture](https://medium.com/@will.streeter/practical-web-development-and-architecture-26a37d04c10f).
Demonstrating how [Docker](https://www.docker.com/)
can be used to assemble a **FullStack integrated development environment** (IDE), four external repositories are
brought together by implementing the use of git submodules. Each submodule contains a **Dockerfile** enabling the manifestation
of its contents as a Docker Image. The docker-compose file in the root of this repository is used to orchestrate both the building
of a Docker Image representing each submodule as well as the 'running' of those Docker Images  as a Docker Containers.


+ [ws-node-demo](https://github.com/WillStreeter/ws-node-demo)
+ [ws-mongo-demo](https://github.com/WillStreeter/ws-mongo-demo)
+ [ws-nginx-demo](https://github.com/WillStreeter/ws-nginx-demo)
+ [ws-ngx-login-demo](https://github.com/WillStreeter/ws-ngx-login-demo)

![Alt Text](https://github.com/WillStreeter/ws-dev-docker-example/raw/master/assets/fullstack.png)

A more detail explanation of how **Dockerfiles** are configured in order to create images and  run them as containers is offered in
the article, [Docker is my {I.D.E}](https://medium.com/@will.streeter/docker-is-my-i-d-e-d6dc84cca26d). In this Docker synopsis, an account of how
docker-compose YAML files can be configured to orchestrate the image creation and container deployment using each of the
submodules' respective Dockerfile can be found. Other aspects of using Docker, such as basic docker commands and common debugging
techniques are delineated in the article as well.


### How to use this example

1. Retrieve this repository and the submodule repositories from GitHub

```
   $> git clone https://github.com/WillStreeter/ws-dev-docker-example.git

   $> git pull && git submodule init && git submodule update && git submodule status
```

2a. Now tat all the repositories and their contents have been downloaded to your machine,
we can simply use the docker-compose commands. I would suggest opening 2 terminals, one for standing up
the entire bundle and another for bringing it down.

```
   //in one terminal we build and stand up the entire suite of docker containers
   $> docker-compose up

   //in a different terminal we can bring the entire suite of docker containers down
   $> docker-compose down

```

 + [localhost  **http://localhost**](http://localhost/#/)

2b. A different approach would be to use the Makefile approach


```
   //in one terminal we build and stand up the entire suite of docker containers
   $> make build-dev

   //and then
   $> make start

   //in a different terminal we can bring the entire suite of docker containers down
   $> make stop

```


 + [localhost  **http://localhost**](http://localhost/#/)



Using the Makefile approach offers the capability of separating the building of images from the running of the images as containers.
This can be very helpful for debugging and isolating where operations and process may be going awry.