 # Digital Ocean

 [Official Docs](https://www.digitalocean.com/docs/)

 [Traversy Media Tutorial](https://www.youtube.com/watch?v=oykl1Ih9pMg&t=3s)

 [Traversy Media Docs](https://gist.github.com/bradtraversy/cd90d1ed3c462fe3bddd11bf8953a896)
 
 - [Create a Droplet](https://www.digitalocean.com/docs/droplets/how-to/create/)
 - [Connect to Droplets with SSH](https://www.digitalocean.com/docs/droplets/how-to/connect-with-ssh/)
 - [Set Up a Node.js Application for Production](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-18-04)
 - [Nginx setup (Optional)](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04)
 - [Initial Server Setup](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04)

# GitHub Actions - Pipeline for deployment

 - [Tutorials](https://www.youtube.com/watch?v=X3F3El_yvFg)
 - Github Repo -> Actions -> Node.js (setup this workflow)
 - Now we will have a **.yml** file
 - This is the action we are going to made -> We can change the branch from here

    ```
    name: Node.js CI

    on:
      push:
        branches: [ 3_docker_production ]
    ```

 - inside jobs build all the task will be done with the push command 
    ```
    jobs:
      build:
    ```
 - We are going to run our virtual private server so use `runs-on: self-hosted`
 - Set specific node js version `node-version: [10.x, 12.x, 14.x, 15.x]`
 - There are some default steps that always going to run 
    ```
    - uses: actions/checkout@v2
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v2
      with:
        node-version: ${{ matrix.node-version }}
    ```
 - At first install all dependencies `- run: npm install`
 - Now run the customs scripts `- run: npm run dev --if-present`
 - production version of our project `- run: npm run build`
 - For express app use pm2 `- run: pm2 restart BackendAPI` (pm2 setup docs below)
 - Now this will not work, so go to setting -> actions -> **add runner**
 - Select OS which web hosting **OS**
 - From the server terminal (where website is hosted ) download everything what is needed
    ```
    # Create a folder
    $ mkdir actions-runner && cd actions-runner
    # Download the latest runner package
    $ curl -o actions-runner-linux-x64-2.277.1.tar.gz -L https://github.com/actions/runner/releases/download/v2.277.1/actions-runner-linux-x64-2.277.1.tar.gz
    # Extract the installer
    $ tar xzf ./actions-runner-linux-x64-2.277.1.tar.gz
    ```
 - Configure
    ```
    # Create the runner and start the configuration experience
    $ ./config.sh --url https://github.com/MdSamsuzzohaShayon/nodejs-yml-github-action --token AELCJXM5ME4WEFYIGCWV5X3AP73QO
    # Last step, run it!
    $ ./run.sh
    ```
 - Using your self-hosted runner
    ```
    # Use this YAML in your workflow file for each job
    runs-on: self-hosted
    ```

 - If there is any error such as <span style="color:red;"> Must not run with sudo</span> -> use `export AGENT_ALLOW_RUNASROOT="1"`
 - Or we can create a user on our server and run all the steps 
 - Configure will ask for name, label etc (we can skip everything default)
 - See all files `ls -la` and execute bash script `./run.sh` 
 - Now go to setting -> actinons - now it's idle and online 
 - GO to Actions tab -> create filename.xml -> From top corner -> re-run all jobs
 - from here we can see everything 
 - From server exit `./run.sh` file and run another bash script `sudo ./svc.sh` -> we can see all the commands here
 - run all commands one by one 
    ```
    sudo ./svc.sh install
    sudo ./svc.sh status
    sudo ./svc.sh start
    sudo ./svc.sh status
    ```
 - It will run on the background


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

### Setup server block for multiple websites

 - Copy nginx default file
   ```
   cd /etc/nginx/sites-available
   ls -la
   sudo cp default somedomain.com
   sudo nano somedomain.com
   ```
 - change servername `server_name _;` to `server_name somedomain.com www.somdomain.com` *point to domain name*
 - edit from nano editor -> Now create symlink `sudo ln -s /etc/nginx/sites-available/somedomain.com /etc/nginx/sites-enabled/` -> Linking to enable sites
 - TO check `sudo nginx -t`
 - Change duplicate default server -> `sudo nano somedomain.com`
   ```
   # REMOVE DEFAULT_SERVER
   listen 80;
   listen [::]:80;
   ```
 - To check `sudo nginx -t` -> if it's is successfull -> `sudo systemctl restart nginx`

### Securing websites
 - [install certbot](https://www.digitalocean.com/community/tutorials/how-to-set-up-let-s-encrypt-with-nginx-server-blocks-on-ubuntu-16-04) -> Let’s Encrypt is a Certificate Authority (CA) that provides an easy way to obtain and install free TLS/SSL certificates,
   ```
   sudo add-apt-repository ppa:certbot/certbot
   sudo apt-get update
   sudo apt install python3-certbot-nginx -y
   ```
 - Allowing HTTPS Through the Firewall (We did it previously - check once again)
   ```
   sudo ufw status
   # IF IT IS DISABLE - ENABLE ONCE AGAIN
   sudo ufw allow 'Nginx Full'
   sudo ufw delete allow 'Nginx HTTP'
   ```
 - Now obtain ssl certificate
   ```
   sudo certbot --nginx -d somedomain.com -d www.somedomain.com
   # IT WILL ASK FOR EMAIL ADDRESS ENT THAT 
   # A FOR AGREE
   # Choose redirect (2)
   ```
 - 




### Domain Setup
 - Domain List -> Domain -> Custom DNS -> Add all digital ochan nameserver -> **ns1.digitalocean.com**, **ns2.digitalocean.com**, **ns3.digitalocean.com** 
 - Go to digital ocean control panel -> Create new record -> **A** -> hostname **@** -> will direct to **IP Address** -> Create record
 - Go to digital ocean control panel -> Create new record -> **A** -> hostname **www** -> will direct to **IP Address** -> Create record


