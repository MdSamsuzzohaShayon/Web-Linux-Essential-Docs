## Docker

 - [Uninstall old docker](https://docs.docker.com/engine/install/ubuntu/#uninstall-old-versions) `sudo apt-get remove docker docker-engine docker.io containerd runc`
 - See the version `sudo docker version`
 - [Uninstall properly](https://docs.docker.com/engine/install/ubuntu/#upgrade-docker-after-using-the-convenience-script) 
    ```
    sudo apt-get purge docker-ce docker-ce-cli containerd.io
    sudo rm -rf /var/lib/docker
    sudo rm -rf /var/lib/containerd
    ```

 - [Install docker once again](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) **Setup repo** [guide](https://linuxhint.com/install_docker_linux_mint/)
 - Remove unwanted packages and update linux system 
    ```
    sudo apt update
    sudo apt autoremove
    ```
 - setup repo `sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release`
 - Add Docker official GPG for linux mint
    ```
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu
    bionic stable"
    ``` 
 - for ubuntu 
    ```
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```

 - Use the following command to set up the stable repository. 
    ```
    echo \
    "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```


#### Docker commands

 - Check version client and server `sudo docker version`
 - 
### [Creating a docker file](https://docs.docker.com/engine/reference/builder/)
 - `FROM node:alpine` -> *The [FROM](https://docs.docker.com/engine/reference/builder/#from) instruction initializes a new build stage and sets the Base Image for subsequent instructions. As such, a valid Dockerfile must start with a FROM instruction.* - From [dockerhub](https://hub.docker.com/_/alpine) search for **alpine** and **node**
 - `COPY . /app` - copy everything to app dir. The [COPY](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.
 - `CMD node app/app.js` - Instruction for executing a command - There can only be one [CMD](https://docs.docker.com/engine/reference/builder/#cmd) instruction in a Dockerfile. If you list more than one CMD then only the last CMD will take effect.The main purpose of a CMD is to provide defaults for an executing container. 
 - `WORKDIR /app` - The [WORKDIR](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any RUN, CMD, ENTRYPOINT, COPY and ADD instructions that follow it in the Dockerfile
 - `sudo docker build -t hello-docker .` <span style="color:yellow;background:#696969;">terminal</span> - [build docker image](https://docs.docker.com/engine/reference/commandline/build/#build-with-path) **-t** for identify, **hello-docker** is the name of our image, **.** is for referancing current dir containing **Dockerfile** - 
 - `sudo docker image ls` <span style="color:yellow;background:#696969;">terminal</span> - [list images](https://docs.docker.com/engine/reference/commandline/image_ls/) seee details about all image
 -  `sudo docker run hello-docker` <span style="color:yellow;background:#696969;">terminal</span> - [Docker runs](https://docs.docker.com/engine/reference/run/) processes in isolated containers
 - `sudo docker pull alpine` <span style="color:yellow;background:#696969;">terminal</span> - Docker Hub contains many pre-built images that you can pull and try without needing to define and configure your own .so we can run it `sudo docker run alpine`
 - `sudo docker run ubuntu` <span style="color:yellow;background:#696969;">terminal</span> - Running ubuntu from docker hub - we can pull it and run it but we can use run command directly if there is no image locally it will pull automitically
 - `sudo docker ps` - [list all the running container](https://docs.docker.com/engine/reference/commandline/ps/) 
 - `sudo docker run -it ubuntu` - run ubuntu container in intractive mode
 - [Removing docker image, container](https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/)
