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
 - cat /etc/hostname




