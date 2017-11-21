
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



### Docker Logs

Find the container name: `docker ps -a`


Live log (from the beginning of the log):
```
docker logs -follow <container_name>
```

Live log (from the last 10 lines of the log):
```
docker logs --follow --tail 10 <container_name>
```