# CentOS
### Installation and setup guide
 - The CentOS Linux distribution is a stable, predictable, manageable and reproducible platform derived from the sources of Red Hat Enterprise Linux (RHEL). 
 - Install centos on virtual box -> open centos -> switch user as root
 - From root user run the command to add user to sudoer group `usermod -aG wheel username` -> change user -> `su - username`
 - Now update and upgrade `yum update kernel` , `yum update && yum upgrade`
 - Set Hostname of Server -> check host `echo $HOSTNAME` -> edit host name `vi /etc/hostname` 
 - Before installing guast addition install some package `sudo dnf install gcc kernel-devel kernel-headers dkms make bzip2 perl`
 - To make it fullscreen -> [install virtualbox guast addition](https://linuxhint.com/install-virtualbox-guest-additions-centos/) -> restart


### Change [Hostname](https://www.tecmint.com/set-change-hostname-in-centos-7/) in CentOS
 - print the groups a user is in `groups`
 - check for existing hostname `hostname` or `cat /etc/hostname` or `ls -la /etc/hostname` 
 - Check the hosts `cat /etc/hosts`
 - Setting hostname temporarily `sudo hostname existing-host-name`
 - To Change hostname permanently `sudo vi /etc/hostname` - change the hostname here
 - Another way to change hostname permanently using `hostnamectl set-hostname your-new-hostname`
 - Update hostname `exac bash` - something it doesn't work
 - check hostname `cat /etc/hostname`
 - Check ping of google dns `google 8.8.8.8` or `ping www.amazon.com`
 - We can also ping our local machine `ping name-of-our-host`
 - create a blackup of this file first `cp /etc/hosts /etc/hosts.backup`
 - Customize this file `sudo vi /etc/hosts` we can set our dns from here
    ```
        # For the localhost
        127.0.0.1   localhost
        # for the host we set earlier
        127.0.1.1   name-of-the-host www.domain.com
    ```
 - now we cna ping `ping localhost` or `ping name-of-the-host www.domain.com` or `127.0.1.1` or `127.0.0.1`
 - `cat /etc/hostname`

### Managing groups
 - When you administer a Linux machine that houses multiple users, there might be times when you need to take more control over those users than the basic user tools offer. This idea comes to the fore especially when you need to manage permissions for certain users. Say, for example, you have a directory that needs to be accessed with read/write permissions by one group of users and only read permissions for another group.
 - Checking the groups of the current users `groups`
 - Change to root `su` check group of particular user `groups username` and check for root `groups` 
 - Exit from root `exit` 
 - See all groups that are available `cat /etc/group` - there are system group which created by default for defferent sofware
 - `groupname:x:1001` here 1001 is the group id
 - Make a group with specific group id `sudo groupadd -g 2099 heroes` and check `cat /etc/group`
 - Add a user to the group `sudo usermod -aG groupname username` we can't see the effect now `groups` 
 - Navigate to root `su` and check `groups username` here we can see groups for the particular user
 - For removing a user from the group `gpasswd -d username groupname`

### Configuring sudo Access
 - The sudo command stands for “Super User DO” and temporarily elevates the privileges of a regular user for administrative tasks. The sudo command in CentOS provides a workaround by allowing a user to elevate their privileges for a single task temporarily.
 - **wheel** is the group where user will have sudo access. check group `groups`, (for ubuntu group name is **sudo**)
 - Add to sudoer or sudo or member of wheel group `sudo usermod -aG wheel username`
 - There is a special file that access to sudo `sudo cat /etc/sudoers` - we should never open this file in text editor and edit it directly
 - But for now I am editing in text  file `sudo vi /etc/sudoers` just to see
 - Instead use `visudo` command to change anythings `sudo visudo /etc/sudoers` here we can see the file name is `sudoers.temp` to open it with nano `sudo EDITOR=nano visudo`
 - Create a new sudoer group as **admin** run `sudo visudo /etc/sudoers`
    ```
        #  ADD THIS LINE BELOW `%WHEEL ALL=(ALL) ALL` TO ALLOW PEOPLE IN TE GROUP ADMIN TO RUN ALL COMMANDS
        %admin ALL=(ALL) ALL
        # THIS FIRST ALL MEANS THAT USER CAN EXECUTE ALL TERMINAL
        # SECOND ALL MEANS MEMBER OF THIS GROUP ADMIN CAN INPERSONATE ALL OTHER USERS
        # THIRD ALL REFERS TO WHAT COMMANDS THE USER OR GROUP ALLOWED TO DO
        # FOR EXAMPLE I WANT TO GIVE PERMISSION ONLY FOR LS COMMANDS
        %admin ALL=(ALL) /usr/bin/ls
    ```
 - Know the full path of a commands `which ls`. depending on shell environment certain directories may or may not be understood as having binary command in them run commands on the linux terminal there are certain directories that are automatically searched for which is why we are able to run ls

 




















