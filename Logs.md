
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



## Docker Logs

Find the container name: `docker ps -a`


Live log (from the beginning of the log):
```
docker logs -follow <container_name>
```

Live log (from the last 10 lines of the log):
```
docker logs --follow --tail 10 <container_name>
```

## Output a live log via http

If you need to share a live log with someone (i.e for support), here is a way to do so.


### Base command 

```
frontail --ui-highlight  --ui-highlight-preset /opt/scripts/frontail/frontail_custom_present.json --theme dark --user seed --password seed <path of log file> &
```

- You may change the user and password. 

- The `&` at the end sends it to the background. 

- You can now see this log at http://serveripaddress:9001. 

- To specify another port, just add: ` --port <port> `



### To create an alias for this:

Edit ~/.bashrc file and add the following (you may change the user and password):
```
## custom aliases
alias ftail='frontail --ui-highlight  --ui-highlight-preset /opt/scripts/frontail/frontail_custom_present.json --theme dark --user seed --password seed '
```

You can now use:

```
ftail <log path> &
```


### Examples:

Normal command:
```
frontail --ui-highlight  --ui-highlight-preset /opt/scripts/frontail/frontail_custom_present.json --theme dark --user seed --password seed /opt/plex_autoscan/plex_autoscan.log &
```

Alias command:
```
ftail /opt/plex_autoscan/plex_autoscan.log &
```
