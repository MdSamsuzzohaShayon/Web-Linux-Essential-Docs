# Nginx

 - [Install on ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04)


### Configure Nginx
 - [Nginx on ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04), [Nginx on ubuntu 18](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04)
 - After installing nginx -> `cd /etc/nginx/sites-available` -> `ls -la` -> **default** is the nginx config file
 - `sudo nano default` -> change the entry point -> `root /var/www/build;` change it to `/var/www;`
 - check everything is valid `sudo nginx -t`
 - Restart nginx `sudo systemctl restart nginx` (it will be forbidden for now)
 - go to the main folder 
   ```
   cd ~ 
   ls -la
   # CHANGE DIRECTRY TO OUR RUNER
   cd actions-runner
   ls -la
   # WE WILL HAVE OUR PROJECT FOLDER
   cd our-project-folder
   ls -la
   # THIS IS THE GITHUB REPOSITORY IT'S CLONING
   cd our-project-folder-github-actions
   ls -la
   pwd
   # COPY THE PATH OF OUR ENTRY POINT FILE
   ```

### For **React.js**
 -  For **React.js** copy the applications path and open nginx default `sudo nano /etc/nginx/sites-available-default`
 - change the entry point `root /var/www;` to `root our/app/path/that/we/have/copid`
 - Once again restart nginx `sudo systemctl restart nginx`
 - From our project folder (no in server) at first `git pull` then change any thing and push it to github -> this should work

### For **Express app** 
 - From server terminal
   ```
   ls -la
   cd express-app-dir
   ls -ls
   cd express-app-dir
   ```

 - We will use **pm2** to run continously `npm install -g pm2` (Change folder permission to use or create seperate global folder- don't use sudo it's not recommanded)
 - Run
   ```
   pm2 start src/app.js --name=backendAPI
   pm2 logs
   ```
 - Make a change and push to github this should work
 - **Setup PORT** -> from server terminal
   ```
   sudo ufw status
   sudo ufw enable
   sudo ufw status
   sudo ufw allow ssh
   sudo ufw 'Nginx Full'
   sudo ufw status
   # Deny port number
   sudo ufw deny 4000
   sudo ufw status
   ```
 - Take advantage of nginx -> use nginx to forward requests
 - Set up location from nginx
   ```
   cd ~
   ls -la
   sudo nano /etc/nginx/sites-available/default
   ```
 - Below **location /{}** create another **location /{}** with same indentation
```
location /api{
   # IT WILL REWRITE THE ROUTE AND CAPTURE EVERY SINGLE ROUTE PARAMETERS
   rewrite ^\/api\/(.*) /api/$1 break;
   proxu_pass  http://localhost:4000
}
```
 - [Test regular expression ](https://regexr.com/) - **All express route need to start with /api** and push to github 
 - Restart nginx `sudo systemctl restart nginx` 
