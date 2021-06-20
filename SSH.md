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

### SSh Beginner
 - SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network.
 - There is two program -> **SSH Server** that need to install on the remote machine, there is also ssh client that need to install on local machine
 - 
