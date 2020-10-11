# NodeJS on Linux

### [Install nodejs](https://github.com/nodesource/distributions/blob/master/README.md#debinstall) on linux mint or ubuntu


```
curl -sL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Remove root previliges from npm

 1. First Method if .npm folder comes with nodejs installation

```
ls -lah /home/shayon/
sudo chown shayon:shayon .npm
``` 

 2. Second Method most effective

```
cd /home/shayon
mkdir .npm
sudo chown -R $(whoami) ~/.npm
```
