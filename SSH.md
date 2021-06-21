# SSH [setup](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2)
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
 - Connect to droplet via terminal and ssh
```
ssh root@150.232.121.122
```

### SSh Beginner - [tutorial](https://www.youtube.com/watch?v=2QXkrLVsRmk&t=275s)
 - SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network.
 - There is two program -> **SSH Server** that need to install on the remote machine, there is also ssh client that need to install on local machine
 - Install **Open SSH server** on [centos](https://linuxconfig.org/install-ssh-server-on-redhat-8) `sudo dnf install openssh-server` 
 - [Some instruction on open ssh](https://linuxhint.com/enable_ssh_centos8/)
```
sudo systemctl status sshd
sudo systemctl start sshd
# enabled to start automatically on system boot
sudo systemctl enable sshd
# change the SSH server configuration files, then for the changes to take effect,
sudo systemctl restart sshd
```
 - Now install and enable the firewall to allow connection [firewalld](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-8), [Install and Setup UFW Firewall on CentOS 8](https://shouts.dev/install-and-setup-ufw-firewall-on-centos-8-rhel-8)
```
sudo dnf install epel-release -y
sudo dnf install ufw -y
sudo ufw enable
sudo ufw status
uso ufw disable
#  UFW Default Policy - By default, the UFW block all incoming traffic and allow all outgoing traffic. 
sudo ufw default allow outgoing
sudo ufw default deny incoming
#  Add Firewall Rules - We can easily add rules in UFW firewall. Let’s open HTTP (80) port
sudo ufw allow http
# or
sudo ufw allow 80
# Now allow ssh
sudo ufw allow ssh
# filter packets based on TCP or UDP
sudo ufw allow 80/tcp
sudo ufw allow 21/udp
# We can deny any incoming and outgoing traffic to any por
sudo ufw deny 8081
#  check the running ports
# method 1
sudo ufw status
# method 2
sudo ufw status numbered
# method 3
sudo ufw status verbose
# Delete Firewall Rules
sudo ufw delete allow http
sudo ufw delete deny 8081
# remove all rules
sudo ufw reset
```
 - Find ip to connect with client `ip a` -> search for inet -> from local machine in terminal `ssh username@ip-address-of-server`
 - 
 




















