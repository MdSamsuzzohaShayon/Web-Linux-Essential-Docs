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
 - Use read only file system for our container using **ro** <span style="background: #2F4F4F; color:#F0FFFF;">terminal </span> so that we can't create any file from docker container
    ```
        sudo docker rm node-app -f
        sudo docker run -v $(pwd):/app:ro -v /app/node_modules -p 3000:3000 -d --name node-app node-app-image
        sudo docker ps
        sudo docker exec -it node-app bash
        touch newfile.txt # touch: cannot touch 'newfile.txt': Read-only file system
        exit
    ```
 - Setting environment variable in docker. in <span style="background: #2F4F4F; color:#F0FFFF;">Dockerfile</span>
    ```
        ENV PORT 3000
        EXPOSE $PORT
    ```
 - Everytime we change in our dockerfile we need rebuild our image - creating environment variable <span style="background: #2F4F4F; color:#F0FFFF;">terminal</span>
    ```
        sudo docker rm node-app -f
        sudo docker ps
        sudo docker build -t node-app-image .
        sudo docker image list
        # --env NAMEOFTHEENVIRONMENVARIABLE=VALUEOFTHEVARIABLE (--env PORT=4000)
        sudo docker run -v $(pwd):/app:ro -v /app/node_modules --env PORT=4000 -p 3000:4000 -d --name node-app node-app-image
        sudo docker exec -it node-app bash
        printenv
        exit
    ```
 - We can use multiple `--env` but for lots of variable we should use **.env** file so create that file and <span style="background: #2F4F4F; color:#F0FFFF;">terminal</span>
    ```
        sudo docker rm node-app -f
        # --env-file ./.env
        sudo docker run -v $(pwd):/app:ro -v /app/node_modules --env-file ./.env -p 3000:4000 -d --name node-app node-app-image
        sudo docker exec -it node-app bash
        printenv
        exit
    ```
 - List all the volumes and delete the preserver volume which is soring for anonimous volume <span style="background: #2F4F4F; color:#F0FFFF;">terminal</span>
    ```
        sudo docker volume ls
        sudo docker volume rm VOLUME_NAME_28743463726ueeyueyrr
        sudo docker volume prune
        EVERYTIME WE DELETE OUR CONTAINER WE SHOULD DELETE THAT VOLUME TOO
        sudo docker rm node-app -fv
    ```
 - Using [docker compose](https://docs.docker.com/compose/) to automate so we don't need to run the docker run everytime manually by command so create **docker-compose.yml** | [version](https://docs.docker.com/compose/compose-file/compose-versioning/) 
 - [Install docker compose](https://docs.docker.com/compose/install/) and open <span style="background: #2F4F4F; color:#F0FFFF;">terminal</span>
    ```
        sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
        sudo chmod +x /usr/local/bin/docker-compose
        # AFTER INSTALL
        sudo docker-compose up --help
        sudo docker-compose up -d
        sudo docker image ls
        sudo docker ps
        sudo docker-compose down -v
    ```

 - Build images before starting containers
    ```
        sudo docker-compose down -v
        sudo docker-compose up --help
        sudo docker-compose up -d --build
    ```

 - Create seperate configuration for development and production
    ```
        sudo docker ps
        # IF ANYTHING RUNNING DELETE EVERYTHING
        sudo docker-compose down -v
        # FOR DEVELOPMENT 
        sudo docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d
        sudo docker-compose -f docker-compose.yml -f docker-compose.dev.yml down -v
        # FOR PRODUCTION - WE DON'T HAVE ANY BIND METHOD SO WE CAN'T SEE ANY CHANGE 
        sudo docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
        # sudo docker-compose -f docker-compose.yml -f docker-compose.prod.yml down -v
        # EVERYTIME WE CHANGE WE NEED TO REBUILD OUR IMGE TO UPDATE IN PRODUCTION
        sudo docker-compose -f docker-compose.yml -f docker-compose.prod.yml down -v --build
        sudo docker exec -it node-docker_node-app_1 bash
        cd node_modules
        ls # WE ARE IN PRODUCTION MODE NODEMON SHOULD NOT BE HERE BUT IT IS STILL HERE
        exit
    ```
 - Change context and argument for production and development
    ```
        sudo docker-compose -f docker-compose.yml -f docker-compose.prod.yml down -v
        sudo docker ps
        sudo docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d --build
        sudo docker-compose -f docker-compose.yml -f docker-compose.dev.yml down -v
        sudo docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d --build
        sudo docker exec -it node-docker_node-app_1 bash
        cd node_modules
        ls # WE ARE IN PRODUCTION MODE NODEMON SHOULD NOT BE HERE BUT IT IS STILL HERE
        exit
    ```