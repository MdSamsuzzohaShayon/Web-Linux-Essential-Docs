# Install Linux without losing D,E,F, ETC

This will only install on C drive

 1. [Installing Ubuntu without deleting other partitons](https://askubuntu.com/questions/536737/installing-ubuntu-without-deleting-other-partitons)
 2. [How to partition my hard disk while installing ubuntu and don't lose data on d,e&g drive?
](https://superuser.com/questions/1215850/how-to-partition-my-hard-disk-while-installing-ubuntu-and-dont-lose-data-on-d-e)
 3. 

# All things to do after installing linux

 1. update 

`sudo apt update && sudo apt upgrade -y`

 2. install essential files for linux

`sudo apt-get install build-essential`

 3. install listed dependincies

```
sudo apt-get install libqt4-dev
sudo apt-get install libjack0
sudo apt-get install libjack-dev
sudo apt-get install libasound2-dev
sudo apt-get install libsndfile1-dev
```

 4. Install additional packagemanager

```
sudo apt install curl
sudo apt install flatpak
```

 5. remove useless files

`sudo apt autoremove`

### See all installed library

`dpkg --list`

# Installation system

### Extract files

```
tar xzf file.tar.gz
tar xjf file.tar.bz2
tar xzvf file.tar.gz
```

### .deb files

```
sudo apt install file_path
sudo dpkg -i file_path
```


