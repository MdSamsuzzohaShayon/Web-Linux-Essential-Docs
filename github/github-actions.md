# Github Actions
 - [Tutorials](https://www.youtube.com/watch?v=Qw2taTafe9k&t=124s)
 - At first create a github repository
 - Create a node js project and push it to github
 - repository -> actions -> nodejs workflow -> setup 
 - this is name and we ca name anything
```name: Node.js CI```
 - **on** is basically just events that we want to listen to so we can update
```
on:
  push:
    branches: [ 2_backend ]
  pull_request:
    branches: [ 2_backend ]
```
 - Execute all the jobs and We can have multiple jobs
```
jobs:
  build:
```
 - To serve on the virtual private server we need to setup runner on our server
```
runs-on: self-hosted
```

 - We can test our code on multiple different version of nodejs and ubuntu
```
    strategy:
      matrix:
        node-version: [14.x]
        # See supported Node.js release schedule at https://nodejs.org/en/about/releases/
```
 - Those are some default setup we should do
```
    steps:
    - uses: actions/checkout@v2
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v2
      with:
        node-version: ${{ matrix.node-version }}
```
 - here CI means clean install at first it will make a clean install of npm
```
    - run: npm install
```
 - It will check for build script in package.json if there is one it will run 
```
    - run: npm run build --if-present
```
 - If we have a start command it will run this start command to run our nodejs app
```
    - run: npm start --if-present
```
 - Now click on start commit -> commit new file
 - and from our local machine project pull all github files 
```
git pull
# or
git pull origin 2_branchname
```
 - Now everytime we will change our project and push it to github and in actions tab we can see the progress
```
git add .
git commit -m "some change on our code from local machine"
git push origin 2_branchname
```
 - Now we have to add runner from github project setting -> actions -> runners (sidebar) -> runners -> self-hosted-runners -> add runner
 - Now go to the hosting server and follow the instructions to donload the project
```
# Create a folder
mkdir email-template-runner.com && cd email-template-runner.com
# Download the latest runner package
curl -o actions-runner-linux-x64-2.278.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.278.0/actions-runner-linux-x64-2.278.0.tar.gz
# Extract the installer
tar xzf ./actions-runner-linux-x64-2.278.0.tar.gz
```
 - Configure our project from hosting server we can set name of runner deployment and name of work folder email-template-runner.com 
```
Create the runner and start the configuration experience
./config.sh --url https://github.com/MdSamsuzzohaShayon/Nodejs-Email-Template --token AELCJXO46GSF7I5BQ5RZOQ3ASHUYW
```
 - now check all files and remove tar file (server terminal inside our runner folder)
```
ls
rm mkdir email-template-runner.com
ls -la
```
 - Now we can run our runner
```
# Last step, run it!
./run.sh
```
 - After creating runner go to github -> actions -> re-run all jobs and seel all the logs
 - from server terminal inside our runner folder
```
ls
# INSIDE OUR RUNNER FOLDER WE SHOULD HAVE ANOTHER FOLDER WITH SAME NAME AS cd email-template-runner.com
cd email-template-runner.com
ls
# HERE ALL OF OUR FILES ARE LOCATED INCLUDING OUR MAIN PROJECT FOLDER (GITHUB PROJECT FOLDER)
cd Nodejs-Email-Template
ls
# HERE WE CAN SEE NODE_MODULES FOLDER IS HERE
npm i pm2
pm2 start --name=EmailTemplate app.js
pm2 log EmailTemplate
```
 - Now in our workflow yaml file run another script in place of node app.js
```
    - run: pm2 restart EmailTemplate
```
 - from server terminal run `pm2 status`
 - From local mechine terminal push our project to github
```
git add .
git commit -m "some change"
git push origin 2_branchname
```
 - Run our runner as a background service from server terminal run
```
ls
# IN OUR MAIN RUNNER FOLDER WE HAVE A .SVC.SH SCRIPT RUN THAT
sudo ./svc.sh install
sudo ./svc.sh start
sudo ./svc.sh status
```
### Nginx
 - Do some nginx stuff
```
sudo ufw status
# ALLOW ANYTHING TO NGINX
sudo ufw allow 5000
```

### [Own github action javascript](https://www.youtube.com/watch?v=a9f2CCU_1uY)