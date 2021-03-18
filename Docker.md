# Docker - A software to create, manage and orchestrate container

## Docker architecture

![Docker architecture](https://docs.docker.com/engine/images/architecture.svg)

## Docker Engine

### Container
- a process has been isolated from all other processes on the host machine 

### Container Image
- an isolate filesystem

#### Common CLI
1. docker image pull
2. docker image ls
3. docker image inspect
4. docker image rm
 
### Dockerfile
- a text-based script used to create a container image.  

#### Instruction

- ENTRYPOINT : 

- RUN : 

#### Common CLI
1. docker container ls 
2. docker container exec
3. docker container stop
4. docker container rm
5. docker container run 
6. docker container inspect

### Common CLI
1. docker ps    
2. docker stop (container-id)
3. docker rm -f (container-id)
4. docker pull (container-id)
5. docker run -it (container-id) /bin/bash  
    -i : running interactively  
    -t : attached to your terminal  
    -d : detached mode (in the backgroud)  
    -p : creating a mapping between the host's port and container's port
    more param to use docker run --help
6. docker exec (container-id)


## Docker Compose
    - use .yaml file to define and run multi-container Docker applications.


## Docker Swarm
    - an orchestration management tool that runs on Docker applications. It helps end-users in creating and deploying a cluster of Docker nodes.


![image](https://docs.docker.com/engine/images/engine-components-flow.png)


> https://docker_practice.gitee.io/zh-cn/image/dockerfile/entrypoint.html

> http://c.biancheng.net/view/3118.html


