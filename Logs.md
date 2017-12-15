
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


Examples:

```
docker logs -f letsencrypt
```

Note: `-follow` = `-f`



## See a live log over http via frontail

[[frontail|https://github.com/mthenw/frontail]] is a Node.js application for streaming logs to the browser (basically a tail -F with an UI).

This is useful in cases you need help and need to show someone from slack support channels your logs. You can mask your IP using ngrok (more on that later).


Steps to do so are as follows:

### Base command 

```
frontail --ui-highlight --ui-highlight-preset /opt/scripts/frontail/frontail_custom_preset.json --theme dark --user seed --password seed <path of log file> &
```

- You may change the user and password. 

- The `&` at the end sends it to the background. 

- You can now see this log at http://serveripaddress:9001. 

- To specify another port, just add: ` --port <port> `



### To create an alias for this:

Edit ~/.bashrc file and add the following (you may change the user and password):
```
## custom aliases
alias ftail='frontail --ui-highlight --ui-highlight-preset /opt/scripts/frontail/frontail_custom_preset.json --theme dark --user seed --password seed '
```

You can now use:

```
ftail --port <port number> <log path> &
```


### To quit the frontail

```
pkill -f frontail 
```

### Examples:

#### Plex Autoscan

```
frontail --port 9001 --ui-highlight --ui-highlight-preset /opt/scripts/frontail/frontail_custom_preset.json --theme dark --user seed --password seed /opt/plex_autoscan/plex_autoscan.log &
```

or via alias..

```
ftail --port 9001 /opt/plex_autoscan/plex_autoscan.log &
```

Log: http://serveripaddress:9001

#### UnionFS Cleaner log 

```
frontail --ui-highlight --port 9002 --ui-highlight-preset /opt/scripts/frontail/frontail_custom_preset.json --theme dark --user seed --password seed /opt/unionfs_cleaner/activity.log &
```

Log: http://serveripaddress:9002


or via alias...

```
ftail --port 9002  /opt/unionfs_cleaner/activity.log &
```

Log: http://serveripaddress:9002


### Use ngrok to hide your IP

If you want to share your log with someone (forums, slack, etc), but don't want to reveal your IP address, you can use ngrok to hide your IP address. 

```
ngrok http <port>
```

It will show you something like this...

![](https://i.imgur.com/74nNEdG.png)

You can now use the `http://XXXXXXXX.ngrok.io` address to share your log. This will be active as long as ngrok is running. To cancel, `ctrl-c`.