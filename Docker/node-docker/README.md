# Node Docker

 - [Tutorial](https://www.youtube.com/watch?v=gm_L69NHuHM)
 - Create **Dockerfile** and do as I did
 - Build our image from <span style="background: #2F4F4F; color:#F0FFFF;">terminal </span>

    ```
        # CREATING DOCKER IMAGE FROM DOCKER FILE - CHECK THE LOG CAREFULLY
        sudo docker build -t node-app-image .

        # CREATE A DOCKER CONTAINER WITH NAME OF NODE-APP
        sudo docker run -d --name node-app node-app-image

        # DELETE DOCKER CONTAINER
        sudo docker rm node-app -f

        # CREATE CONTAINER ONCE AGAIN 
        sudo docker run -p 3000:3000 -d --name node-app node-app-image

        # REDIRECTING TRAFFIC AND SETUP PORT - ALL THE TRAFFIC FOR WINDOWS OR LINUX PORT 4000 WILL BE SEND TO DOCKER PORT 3000
        sudo docker run -p 4000:3000 -d --name node-app node-app-image
    ```
 - Now go to browser and __localhost:4000__ this will work
 - `sudo docker exec -it node-app bash` <span style="background: #2F4F4F; color:#F0FFFF;">terminal </span> The [docker exec](https://docs.docker.com/engine/reference/commandline/exec/) command runs a new command in a running container.
    ```
        # DOCKER FILE SYSTEM
        ls
        exit
        sudo docker rm node-app -f
    ```
 - Create a **.dockerignore** file and list all the unwanted file this is same as **.gitignore** 
 - Once again rebuild our image <span style="background: #2F4F4F; color:#F0FFFF;">terminal </span>
    ```
        sudo docker build -t node-app-image .
        sudo docker run -p 4000:3000 -d --name node-app node-app-image
        sudo docker ps
        # ONCE AGAIN OPEN INTRACTIVE SHELL 
        sudo docker exec -it node-app bash
        ls
    ```
 - If we change anything in our code we need rebuild our image to update it  <span style="background: #2F4F4F; color:#F0FFFF;">terminal </span>
    ```
        sudo docker ps
        sudo docker rm node-app -f
        sudo docker build -t node-app-image .
        sudo docker image ls
        sudo docker run -p 3000:3000 -d --name node-app node-app-image
    ```
 - Sync a folder in our local host machine so that we don't have to continuously rebuild our image everytime we update our code <span style="background: #2F4F4F; color:#F0FFFF;">terminal </span>
    ```
        # DELETE CONTAINER
        sudo docker rm c1b4f2524cd4 -f
        # sudo docker run -v pathtofolderonlocation:pathtofolderoncontainer -p 3000:3000 -d --name node-app node-app-image
        # sudo docker run -v /home/shayon/Documents/Web-Linux-Essential-Docs/Docker/node-docker/:/app -p 3000:3000 -d --name node-app node-app-image
        # ALTERNATIVELY WE CAN USE VARIABLE (for windows use %cd%)
        sudo docker run -v $(pwd):/app -p 3000:3000 -d --name node-app node-app-image
        sudo docker exec -it node-app bash
        more changed-file-dir.js
        exit
        sudo docker ps
        sudo docker rm node-app -f
    ```
 - From **Dockerfile** change the command for nodemon and rebuild image once again <span style="background: #2F4F4F; color:#F0FFFF;">terminal </span>
    ```
        sudo docker build -t node-app-image .
        sudo docker rm node-app -f
        sudo docker run -v $(pwd):/app -p 3000:3000 -d --name node-app node-app-image
    ```
 - `sudo docker logs node-app` <span style="background: #2F4F4F; color:#F0FFFF;">terminal </span>
 - Create a new volume to prevent deleting **node_modules** 
    ```
        sudo docker rm node-app -f
        sudo docker run -v $(pwd):/app -v /app/node_modules -p 3000:3000 -d --name node-app node-app-image
        sudo docker ps
    ```
 - We will not use bind mount **-v** in production mode
 - 51:00
