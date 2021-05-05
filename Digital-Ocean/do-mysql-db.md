# MySql on Digital Ocean

### Option 1 (Creating seperate database )
 - Go to digital ocean dashboard -> create -> database -> (We can set everything default or we can change)
 - Select the project -> create db cluster (It could take some time)
    1. create db cluster -> get started 
    2. secure db cluster -> add trusted source would be our droplet (we can also select your current computer ip to access from our computer) 
    3. Connection details -> all the details to access our database -> flags -> by using this connect database from cli
    4. complete step 4 and go to overview page
 - connect database from terminal 
```
show databasesl
show tables;
```

### Option 2 ( install mysql in linux server)
 - [Tutorials](https://www.youtube.com/watch?v=Wqv14Wi6ZHU) [See the docs](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04) We can do the same thing for aws, linode or any other machine
```
sudo apt update
sudo apt install mysql-server
sudo mysql_secure_installation
# validate password plugin -> yes
# set a lavel  of password validation policy
# STRONG: 0 -> setting the first option
# continue with password that is provided -> n
# remove anonymious user -> y
# disallow root login remotly -> y
# NOW RUN MYSQL ON TERMINAL
sudo mysql
```
 - MySql congifure from mysql shell
```
CREATE USER 'shayon'@'localhost' IDENTIFIED BY "md-shayon";
GRANT ALL PRIVILEGES ON *.* TO 'shayon'@'localhost';
FLUSH PRIVILEGES;
```

 - Try to login from server terminal
```
mysql -u shayon -p
# MYSQL SHELL
CREATE DATABASE someDbName
show databases;
CREATE TABLE Users (id VARCHAR(100) NOT NULL PRIMARY KEY, name VARCHAR(100), age SMALLINT)
describe users;
INSERT INTO Users VALUES ('1', 'someName', )
```

### Option 3 (Connect with MySQL WorkBench)
 - [Tutorial](https://www.youtube.com/watch?v=lTSWvpwdhcE)
 - Digital ocean dashboard -> create -> droplet -> instead of ubuntu select **one-click apps** -> select required software we need to install 
 - We can get all the credentials via email to connect mongodb database
 - In digital ocean dashboard -> droplet show option -> access console (we can use terminal as well)
 - Reset password if it asked -> we are in our ubuntu server and we can see phpmyadmin user and password 
 - Open mysql work beanch and create a new connection -> set a name -> connection method **Standard (TCP/IP)** since we didn't setup ssh
 - host name will be droplet public ip, port is as usual 3306
 - Store in valut -> set password for root user
 - Create a new user using phpmyadmin ->







