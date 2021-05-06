# Host website on cent os

<h2 style="color:#000033; background:  #ccccff; padding: 10px auto;">Step 1 - Connect to the server via ssh</h2>

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




<hr />

 - Some problems regarding hosting
How to connect to digital ocean
https://linuxize.com/post/how-to-add-user-to-sudoers-in-centos/
user is not sudoers file ubuntu
Unable to add a new user to the sudo group [duplicate]
https://unix.stackexchange.com/questions/591420/usermod-group-sudo-does-not-exist-in-centos
Must not run with sudo while trying to create a runner
https://serverfault.com/questions/1052695/must-not-run-with-sudo-while-trying-to-create-a-runner-using-github-actions

