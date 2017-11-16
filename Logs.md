
## Plex Autoscan


Check Status:
```
sudo systemctl status plex_autoscan.service
```

Live Log:
```
tail -f /opt/plex_autoscan/plex_autoscan.log
```
or
```
sudo journalctl -fu plex_autoscan.service
```

## UnionFS Cleaner


Check Status:
```
sudo systemctl status unionfs_cleaner.service
```


Live Log:
```
tail -f /opt/unionfs_cleaner/activity.log
```
or
```
sudo journalctl -fu unionfs_cleaner.service
```

## Plexdrive

Check Status:
```
sudo systemctl status plexdrive.service
```


See a live log:
```
sudo journalctl -fu plexdrive.service
```

## UnionFS

Check Status:
```
sudo systemctl status unionfs.service
```


See a live log:
```
sudo journalctl -fu unionfs.service
```



## Docker containers

Find the container name: `docker ps -a`


Live log:
```
docker logs -f <container_name>
```