# [Docker](https://docs.docker.com/get-started/overview/)
 - [Tutorial](https://www.youtube.com/watch?v=Gw2Jrid4SaQ) [Docs](https://docs.docker.com/get-started/overview/)
 - *Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production.*

### [Docker Image](https://jfrog.com/knowledge-base/a-beginners-guide-to-understanding-and-building-docker-images/#:~:text=A%20Docker%20image%20is%20a,publicly%20with%20other%20Docker%20users.)

 - *A Docker image is a read-only template that contains a set of instructions for creating a container that can run on the Docker platform. It provides a convenient way to package up applications and preconfigured server environments, which you can use for your own private use or share publicly with other Docker users.*

### [Docker container](https://www.docker.com/resources/what-container)
 - *A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.*



### [Install on Windows](https://docs.docker.com/docker-for-windows/install/)

### [Install on Linux](https://docs.docker.com/engine/install/ubuntu/)

### Using Docker
 - Docker help
```
sudo docker --help
```
 - See version of docker
 ```
    sudo docker version
 ```

 - Pull image from internet and run
 ```
    sudo docker run hello-world
 ```

 - Pull an image from dockerhub [**whalesay**](https://hub.docker.com/r/docker/whalesay)
 ```
    sudo docker run docker/whalesay cowsay Hello-World!
 ```
 - busybox commands
```
    sudo docker run busybox
    sudo docker run busybox echo hello Shayon
    sudo docker run busybox ping google.com
    // ALL FILES AND FOLDER OF FILE SYSTEM SNAPSHORT
    sudo docker run busybox ls
    sudo docker run busybox sh
```
 - Show all the containers informations
```
docker ps
docker ps --all
```
 - Stop a specific tontainer
```
docker stop CONTAINER_ID
//OR
docker kill CONTAINER_ID
```
 - Create a new container and start container 
```
docker create hello-world
sudo docker start -a SOME_ID_PREVIOUSLY_GOT
```
 - Show all details of a container
```
sudo docker logs CONTAINER_ID
```
 - Open shell inside a container (Ctrl + D to get out of shell)
```
sudo docker exec -i -t CONTAINER_ID sh
ls
cd ..
pwd
ls
```

### [Dockerfile](https://docs.docker.com/engine/reference/builder/)
 - *Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build users can create an automated build that executes several command-line instructions in succession. This page describes the commands you can use in a Dockerfile. When you are done reading this page, refer to the Dockerfile Best Practices for a tip-oriented guide.*
 - Buillding a container with dockerfile create a file with name **Dockerfile**.
```
FROM alpine

RUN apk add --update redis

CMD ["redis-server"]
```
 - Making container with simple command 
```
docker build .
//OR
sudo docker build -t shayon/redis:latest .
docker run CONTAINER_ID
sudo docker run shayon/redis
```
 - Running same thing in alpine shell(Ctrl + D)
 ```
 sudo docker run -it alpine sh
 ls 
 pwd
 apk add --update redis
 ```
 - 


