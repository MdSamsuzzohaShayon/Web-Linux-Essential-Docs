# Install Linux without losing D,E,F, ETC

This will only install on C drive

 1. [Installing Ubuntu without deleting other partitons](https://askubuntu.com/questions/536737/installing-ubuntu-without-deleting-other-partitons)
 2. [How to partition my hard disk while installing ubuntu and don't lose data on d,e&g drive?
](https://superuser.com/questions/1215850/how-to-partition-my-hard-disk-while-installing-ubuntu-and-dont-lose-data-on-d-e)
 3. 

# All things to do after installing linux

 1. update 

```
sudo apt update && sudo apt upgrade && sudo apt dist-upgrade && sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade -y
```

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

### Tarball file

 1. Extract
```
tar xzf file.tar.gz
tar xjf file.tar.bz2
tar xzvf file.tar.gz
xz -d file.txz
```

 2. read README or Install file
 3. go to file directory and run the command

```
./configure
make
sudo make install
```

### .deb files

```
sudo apt install file_path
sudo dpkg -i file_path
```

### flatpak

```
flatpak install https://flathub.org/repo/appstream/org.gimp.GIMP.flatpakref
flatpak run org.gimp.GIMP//stable
flatpak update
```

[Flatpak official installation guide](https://flatpak.org/setup/Ubuntu/)



### Installing custom folder color

```
sudo add-apt-repository ppa:costales/folder-color
sudo apt-get update
sudo apt-get install folder-color
nautilus -q
```

now just right click on any folder and can find a color option
