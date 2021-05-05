# Linode hosting
 - Go to linode dashboard -> create -> linode -> choose a distribution -> ubuntu -> set a root password -> add an ssh key -> (keep rest of them default)
 - linode server -> summery (we have 2 ip address) -> Networking -> we have ssh access -> copy ssh and paste into the terminal
 - from terminal of ubuntu server
```
sudo apt update
sudo apt htop
# SUMMARY OF OUR LINUX SYSTEM
htop
```
 - Install nginx for serving static files -> in browser paste ip address -> *nginx by default runs on port 80*
```
sudo apt install nginx
service nginx status
```
 - Install mongodb, node js and git
```
sudo apt install mongodb
service mongodb status
sudo apt install nodejs
sudo apt install npm
npm install -g -n
n 12
node -v
sudo apt install git
```
 - Clone github repo from server and run the project
```
git clone github-repo/some-project-name.git
ls
cd some-project-name
npm install
node server.js
```
 - From browser open the url with ip and port number example: __198.58.99.82:4000__
 - Nginx to server static file 
```
exit
ls -la
cd some-project-name
ls -la
cd public
pwd
# COPY THE PATH OF STATIC FILES
cd /etc/nginx/sites/available
nano default 
```
 - Change the root of the project
```
# SET STATIC FILE PATH IN NGINX
root /root/some-project-name/public;
```
 - now restart nginx
```
sudo service nginx status
sudo service nginx restart
```
 - Now we may can't access __198.58.99.82:4000__ 
```
cd /etc/nginx
ls -la
nano nginx.conf
# IN TEXT EDITOR 
user root
# EXIT FROM EDITOR
sudo service nginx restart
```
 - Using pm2 for running nodejs continuously
```
npm install -g pm2
cd /root/some-project-name
pm2 start app.js
pm2 status
```
 - Set a proxy pass in nginx and node js
```
cd /etc/nginx/sites-available
nano default
# IN TEXT EDITOR 
# BELOW LOCATION
location /api {
    proxy_pass http://localhost:4000
}
# EXIT FROM EDITOR
service nginx restart
```
 - Get rid of the port of nodejs app from our project change this and push to github
```
app.listen(4000, "localhost", ()=> console.log("server is running"));
```
 - from linux server terminal 
```
cd /root/some-project-name
git pull
# OR
git pull origin master
pm2 restart app.js
```