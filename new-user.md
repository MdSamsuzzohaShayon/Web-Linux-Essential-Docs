# New User Linux
 - There is two option to create user 
 	1. `adduser` this is simple and easiest way
 	2. `useradd` little bit harder but this is the best way
 - Creating a new user
```
sudo useradd -g users -G sudo -s /bin/bash -m -c "User Full Name" someusername
```
 - explaining everything
```
sudo useradd \ # CREATING A NEW USER
	-g users \ # ADD USER TO USER GROUP
	-G sudo \ # ADDING USER TO SUDO GROUP SO USER CAN USE SUDO
	-s /bin/bash \ # USE BASH AS DEFAULT SHELL ENVIRONMENT
	-m \ # CREATING A HOME FOLDER
	-c "User Full Name" \ # SETTING FULL NAME
	someusername # SETTING MAIN USER NAME
```
 - Set password for user
```
sudo passwd someusername
```
 - Switch user in terminal only
```
su - someusername
```
 - Delete a user 
```
sudo userdel someusername
```
