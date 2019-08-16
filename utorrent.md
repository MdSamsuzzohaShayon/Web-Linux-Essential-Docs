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
