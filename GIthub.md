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