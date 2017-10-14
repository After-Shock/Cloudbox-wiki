## Can I install this on an ARM machine?

  - ARM is not supported.

## Don't want a certain docker app?

Via Command line:
- Get a list of docker container's installed: `docker ps -a`  
- Remove the one you don't want (where `<name>` is replaced with the docker container's name): `docker stop <name> && docker rm <name>`
- Note: Be careful not to remove any container that is essential to Cloudbox (e.g. `nginx-proxy`, `letsencrypt-nginx-proxy-companion`, etc)

Via Portainer:
- https://portainer._yourdomain.com_
- "Containers" --> make your selection --> "Remove"


## Does Cloudbox support encryption data on Google Drive?

  - In short, no.

## Why does Cloudbox not support encryption data on Google Drive?

 - While there are pro's and cons for using either encrypted or unencrypted data on cloud services, Cloudbox developer(s) have decided to not support encrypted cloud data. 

 - Note: You may be able to modify Cloudbox to use encrypted data stored on the cloud (see [here](https://github.com/dweidenfeld/plexdrive/blob/master/TUTORIAL.md)), but that will be on you to setup yourself with no support from us.

## Does Cloudbox support any other cloud storage provider other than Google Drive?

 - In short, no.

 - Note: You may be able to modify Cloudbox to use another cloud storage provider (see [here](https://rclone.org/commands/rclone_mount/)), but that will be on you to setup yourself with no support from us.


## Unrar module fails to install during the Common Role step


  1. Edit the Common Task role:

      ```
      nano ~/cloudbox/roles/common/tasks/main.yml
      ```

  1. Replace `unrar` with `unrar-free` under the `Install common packages` section (below `with_items:`)

      ```
      - name: Install common packages
         apt: "name={{item}} state=installed"
         with_items:

      ```
  1. `ctrl-x` and `y` to save

## pip ssl error

   - Run `sudo easy_install pyOpenSSL` and retry.


## Error Connecting:  Error while fetching server API version: Timeout value connect was Timeout(connect=60, read=60, total=None), but it must be an int or float.

  - Run `sudo pip install requests==2.10.0` and retry.

## Issues with ipv6 / disabling ipv6

  - Run `sudo nano /etc/sysctl.conf` and add these lines (`ctrl-x` and `y` to save)

    ```
    net.ipv6.conf.all.disable_ipv6 = 1
    net.ipv6.conf.default.disable_ipv6 = 1
    net.ipv6.conf.lo.disable_ipv6 = 1
    ```
  - Then run `sudo sysctl -p`

## If during the first time setup, you switched the order of Plex libraries (i.e TV first then Movies)

  You will need to get the Plex section IDs and replace them in the Plex Autoscan config:

  1. Getting the Run `/opt/plex_autoscan/scan.py sections` to list the section IDs.

  1. Edit the Plex Autoscan config via `nano /opt/plex` and switch the ID numbers to match the Section IDs from Step 1.

  1. Restart Plex Autoscan: `sudo nano systemctl restart plex_autoscan`   

## PlexPy logs location:

  - If you are asked for the plex logs location, it is exactly `/logs`.

## Change shell of user account to bash:

How to check current shell:

```shell
echo $0
-sh
```

or

```shell
echo ${SHELL}
/bin/sh
```

Run this command to set bash as your shell (where `<user>` is replaced with your username):

```
sudo chsh -s /bin/bash <user>
sudo reboot
```

## During Cloudbox install, get the message "403 Client Error: Forbidden: endpoint with name <container name> already exists in network <network name>":

You have a remnant of the container in the Docker's network. Verify with the command below (where `<network name>` and `<container name>` is replaced with the network name and container name mentioned in the error, respectively):
```
docker inspect network <network name> | grep <container name>
```

To remove the remnant, run this command and try again:

```
docker network disconnect -f <network name> <container name>
```


## During Cloudbox install, get the message "500 Server Error: Internal Server Error: driver failed programming external connectivity on endpoint <container name>: Bind for 0.0.0.0:<port number> failed: port is already allocated":

```
sudo service docker stop
sudo service docker start
```


## Newly downloaded stuff in Sonarr and Radarr is not being added to Plex?

- Test another download and run the following command:
  ```
   tail -f /opt/plex_autoscan/*.log
  ```

- If you see this...

   ```
   terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
   boost::filesystem::create_directories: Permission denied: "/config/Library/Logs"
   ```

  There is an issue with the permissions on that folder that you'll need to fix manually (Cloudbox can't fix this as Plex creates this folder after the first scan)

   To fix this, Run the following:

   ```
   docker stop plex
   sudo chown -R seed:seed /opt/plex
   docker start plex
   ```
  

   Example of a successful scan:

   ```
   2017-10-10 17:48:26,429 -    DEBUG -      PLEX [ 6185]: Waiting for turn in the scan request backlog...
   2017-10-10 17:48:26,429 -     INFO -      PLEX [ 6185]: Scan request is now being processed
   2017-10-10 17:48:26,474 -     INFO -      PLEX [ 6185]: No 'Plex Media Scanner' processes were found.
   2017-10-10 17:48:26,474 -     INFO -      PLEX [ 6185]: Starting Plex Scanner
   2017-10-10 17:48:26,475 -    DEBUG -      PLEX [ 6185]: docker exec -u plex -i plex bash -c 'export LD_LIBRARY_PATH=/usr/lib/plexmediaserver;/usr/lib/plexmediaserver/Plex\ Media\ Scanner --scan --refresh --section 1 --directory '"'"'/data/Movies/Ravenous (1999)'"'"''
   2017-10-10 17:48:33,712 -     INFO -     UTILS [ 6185]: GUI: Scanning Ravenous (1999)
   2017-10-10 17:48:33,959 -     INFO -     UTILS [ 6185]: GUI: Matching 'Ravenous'
   2017-10-10 17:48:38,556 -     INFO -     UTILS [ 6185]: GUI: Score for 'Ravenous' (1999) is 117
   2017-10-10 17:48:38,607 -     INFO -     UTILS [ 6185]: GUI: Requesting metadata for 'Ravenous'
   2017-10-10 17:48:38,705 -     INFO -     UTILS [ 6185]: GUI: Background media analysis on Ravenous
   2017-10-10 17:48:39,201 -     INFO -      PLEX [ 6185]: Finished scan!
   ```




## Don't see your Gdrive files in /mnt/plexdrive?

### Check on status

```
sudo systemctl status plexdrive
```

### Error: `Process: XXXXX ExecStop=/bin/fusermount -uz /mnt/plexdrive (code=exited, status=217/USER)`

This could happen if you already had a user account on the server before adding it to settings.yml. You simply need to edit 3 files located in `/etc/systemd/system/` (`plex_autoscan.service`, `plexdrive.service`, and `unionfs.service`)

like this...
```
sudo nano /etc/systemd/system/plexdrive.service
```

and change `User` and `Group` under `[Service]` to match yours' (run `id` on command prompt to check):

```
[Service]
User=yourusername
Group=yourgroupname
```

After editing all three files...reload systemctl:

```
sudo systemctl daemon reload
```

And restart the services:

```
sudo systemctl restart plexdrive.service
sudo systemctl restart plex_autoscan.service
sudo systemctl restart unionfs.service
```
