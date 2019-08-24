## Installing uTorrent

```
cd ~/Downloads/
sudo tar -xvzf utserver.tar.gz -C /opt/
sudo chmod -R 755 /opt/utorrent-server-alpha-v3_3/
sudo ln -s /opt/utorrent-server-alpha-v3_3/utserver /usr/bin/utserver
```

## Start uTorrent

```
utserver -settingspath /opt/utorrent-server-alpha-v3_3/
sudo apt-get install libssl0.9.8:i386
localhost:8080/gui
```

## Uninstall uTorrent

`sudo rm -r /opt/utorrent-server-alpha-v3_3 /usr/bin/utserver`


[know more](https://askubuntu.com/questions/530955/how-to-install-utorrent-v3-3-on-14-04/530961)
[more](http://ubuntuhandbook.org/index.php/2016/09/setup-%CE%BCtorrent-server-ubuntu-16-04/)
