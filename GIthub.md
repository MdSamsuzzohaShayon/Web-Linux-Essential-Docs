# Static website hosting on github 

 - Anything doesn't have backend (react, vanilla are also useable)
 - We will use [gh-pages](https://github.com/tschaub/gh-pages)
 - Gh-page will create a seperate branch 
 - make a folder and take all final deployment file there

## Using gh-pages

 - `npm init -y` 
 - `npm install gh-pages` 
 - in **package.json** add a homepage property below licence property (homepage property below)
 - ` "homepage":"https://MdSamsuzzohaShayon.github.io/portfolio" `
 - Create script to deploy below test property
 - ` "deploy": "gh-pages -d dist" `
 - create a git for the project and upload that to the github
 - Run this cmd "npm run deploy"

## Easy way
 - Go to setting of github project
 - github pages -> source -> Select a publishable page 

## Add custom domain
 - Purchase a domain and add some records
 - add similler ip address by increasing one
 - Example: 

![domain list](img/domain_list.png)

 - Change cname and redirect record

 - Go to setting of github project
 - github pages -> custom domain

## Github Desktop Application

 - Download Github Desktop Application -> sign in
 - Create new repo and publish it to github
 - name: **username.github.io**
 - Copy all of my file and paste it to **username.github.io** folder
 - For creating folder first we will create path for our website and there will be **username.github.io**
 - Write something in summery
 - Publish repository


[*Frok a repo*](https://help.github.com/en/articles/fork-a-repo)


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





### Domain Setup
 - Domain List -> Domain -> Custom DNS -> Add all digital ochan nameserver -> **ns1.digitalocean.com**, **ns2.digitalocean.com**, **ns3.digitalocean.com** 
 - Go to digital ocean control panel -> Create new record -> **A** -> hostname **@** -> will direct to **IP Address** -> Create record
 - 











































