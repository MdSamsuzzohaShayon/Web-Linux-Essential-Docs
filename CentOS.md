# CentOS
### Installation and setup guide
 - The CentOS Linux distribution is a stable, predictable, manageable and reproducible platform derived from the sources of Red Hat Enterprise Linux (RHEL). 
 - Install centos on virtual box -> open centos -> switch user as root
 - From root user run the command to add user to sudoer group `usermod -aG wheel username` -> change user -> `su - username`
 - Now update and upgrade `yum update kernel` , `yum update && yum upgrade`
 - Set Hostname of Server -> check host `echo $HOSTNAME` -> edit host name `vi /etc/hostname` 
 - Before installing guast addition install some package `sudo dnf install gcc kernel-devel kernel-headers dkms make bzip2 perl`
 - To make it fullscreen -> [install virtualbox guast addition](https://linuxhint.com/install-virtualbox-guest-additions-centos/) -> restart


