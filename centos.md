# Host website on cent os

### Step 1 - Connect to the server via ssh

 - SSH [setup](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2)
 - During creating instance or droplet we have additional options that is **IPv6, user data, monitoring** (we can uncheck them)
 - From terminal generate a ssh key
```
cd ./ssh
ssh-keygen
# set filename
# no need passphrase
ls -la
less filename.pub
# COPY THE KEY
```
 - In authentication section -> (We can set password and login with it but ssh option is more secure) create new ssh key -> paste the ssh key in the content field -> set a name -> check that ssh key
 - alternativly inside server we can paste that ip address
```
cat ~/.ssh/id_rsa.pub | ssh demo@198.51.100.0 "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys"
```
 - We can disable password for root
```
sudo nano /etc/ssh/sshd_config
# CHANGE IT INSIDE TEXT EDITOR
PermitRootLogin without-password
# To put these changes into effect
sudo systemctl reload sshd.service

```
 - Connect to droplet via terminal and ssh
```
ssh root@150.232.121.122
```

### Step 2 - Setup server
 - Get some system informations
```
# network hostname
uname -n
# get information about kernel-version
uname -v
# summary of your hardware information
sudo lshw -short
# check os version
cat /etc/os-release
lsb_release -a
hostnamectl
```
 - Update our system
```
# check internet
ping 8.8.8.8
# update our system
sudo yum update

```
 - Set hostname
```
# echo $HOSTNAME --------->check current HOSTNAME
nano /etc/hostname ` --------->
# edit and replace old hostname with your own # echo $HOSTNAME --------->logout and login again  
```

### Step 3 - Create a new centos user
 - [List all user](https://www.liquidweb.com/kb/list-users-centos-7/)
```
# list all user including system user
cut -d: -f1 /etc/passwd
getent hosts
```
 - Add a [new user](https://github.com/MdSamsuzzohaShayon/Web-Linux-Essential-Docs/blob/5_linux_for_beginner/new-user.md)

```
sudo useradd -g users -s /bin/bash -m -c "User Full Name" someusername
# Set password for user
sudo passwd someusername
# Switch to new user
su - someusername
```

 - Add [users to sudoers](https://phoenixnap.com/kb/how-to-create-add-sudo-user-centos) in cent os
```
# Verify the Wheel Group is Enabled
# Scroll through the configuration file until you see the following entry - and remove # from beganning and uncomment it
%wheel        ALL=(ALL)       ALL
# To add a user to the wheel group
usermod –aG wheel UserName
```
 - Alternative way to add user to sudoers
```
cat /etc/sudoers
nano /etc/sudoers
# Allow root to run any commands anywhere
root ALL=(ALL) ALL
UserName ALL=(ALL) ALL
```
 - Check sudo previlages 
```
# Switch to the new
su - UserName
# check sudo 
sudo ls -la /root
```

### Step 4 - Install github runner 
 - Solve must be sudo user problem
```
# The env variable to use is RUNNER_ALLOW_RUNASROOT="1" You can :
# Export it before running config.sh using 
export RUNNER_ALLOW_RUNASROOT="1"
# Start config.sh like this : 
RUNNER_ALLOW_RUNASROOT="1" ./config.sh --url...

```

### Step 5 - Install  all essential things
 - Install [nodejs on cent os](https://nodejs.org/en/download/package-manager/#centos-fedora-and-red-hat-enterprise-linux) - [nodejs installation method](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-centos-8)
```
node --version
npm --version
# dnf module install nodejs:<stream>
dnf module install nodejs:<stream>
# where <stream> corresponds to the major version of Node.js. To see a list of available streams:
dnf module list nodejs
For example, to install Node.js 12:
dnf module install nodejs:12
node --version
npm --version
sudo npm install -g npm
```
 - Install [mysql on cent os](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-centos-7) - we nee A CentOS 7 with a non-root user with sudo privileges. - [Alternative way](https://www.mysqltutorial.org/install-mysql-centos/)
```
# CHECK MYSQL IS PREVIOUSLY INSTALLED OR NOT
sudo systemctl status mysqld

# In a web browser, visit: https://dev.mysql.com/downloads/repo/yum/
# DOWNLOAD FILE USING WGET
wget https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
# verify the integrity of the download by running md5sum
md5sum mysql80-community-release-el7-3.noarch.rpm
# install the package
sudo rpm -ivh mysql80-community-release-el7-3.noarch.rpm
This adds two new MySQL yum repositories
sudo yum install mysql-server
```
 - Starting MySQL
```
# start the daemon with the following command
sudo systemctl start mysqld
# to be sure we succeeded
sudo systemctl status mysqld
# During the installation process, a temporary password is generated for the MySQL root user.
sudo grep 'temporary password' /var/log/mysqld.log
```
 - Configuring MySQL
```
# Use this command to run the security script.
sudo mysql_secure_installation
# This will prompt you for the default root password. As soon as you enter it, you will be required to change it.
```
 - [Install and Secure phpMyAdmin](http://digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-with-apache-on-a-centos-7-server) -  Unfortunately, phpMyAdmin is not available in CentOS 7’s default repository. To get the packages we need, we’ll have to add an additional repo to our system. The EPEL repo (Extra Packages for Enterprise Linux) 
```
sudo yum install epel-release
# install the phpMyAdmin package using the yum
sudo yum install phpmyadmin
```
 - Open the file in your text editor now so that we can make a few changes. Change any lines that read Require ip 127.0.0.1 or Allow from 127.0.0.1 to refer to your home connection’s IP address
```
sudo nano /etc/httpd/conf.d/phpMyAdmin.conf
```


### Step 6 - Install and setup nginx

 - [Install nginx](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-8) on cent os





<hr />

 - Some problems regarding hosting

How to connect to digital ocean
https://linuxize.com/post/how-to-add-user-to-sudoers-in-centos/
user is not sudoers file ubuntu
Unable to add a new user to the sudo group [duplicate]
https://unix.stackexchange.com/questions/591420/usermod-group-sudo-does-not-exist-in-centos
Must not run with sudo while trying to create a runner
https://serverfault.com/questions/1052695/must-not-run-with-sudo-while-trying-to-create-a-runner-using-github-actions


- test
    1. create a simple runner inside cent os
    2. hosting nodejs in cent os server
