## Can I install this on an ARM machine?

ARM is not supported.


## If you are using a Scaleway server...

1. Choose an X86 server (vs ARM). 

1. Select "Ubuntu Xenial" as the distribution. 

1. Click the server on the list. 

1. Under "ADVANCED OPTIONS", click "SHOW". 

1. Under "BOOTSCRIPT", select `x86_64 4.10.8 docker #1`. 

   ![](https://i.imgur.com/MrgL8mN.png)

   ![](https://i.imgur.com/8cfqjnR.png)

1. You can now start the server. 

1. You can skip [[updating the kernel|Updating Kernel]]. 

Reference: https://www.scaleway.com/docs/bootscript-and-how-to-use-it/


## Does Cloudbox support encryption data on Google Drive?

In short, no.

## Why does Cloudbox not support encryption data on Google Drive?

While there are pro's and cons for using either encrypted or unencrypted data on cloud services, Cloudbox developer(s) have decided to not support encrypted cloud data. 

Note: You may be able to modify Cloudbox to use encrypted data stored on the cloud (see [here](https://github.com/dweidenfeld/plexdrive/blob/master/TUTORIAL.md)), but that will be on you to setup yourself with no support from us.

## Does Cloudbox support any other cloud storage provider other than Google Drive?

In short, no.

Note: You may be able to modify Cloudbox to use another cloud storage provider (see [here](https://rclone.org/commands/rclone_mount/)), but that will be on you to setup yourself with no support from us.


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
  1. `Ctrl-x`, `y`, and `enter` to save.


## pip ssl error

   - Run `sudo easy_install pyOpenSSL` and retry.


## If you are unable to find your Plex server

You may resolve this by either

 - Installing Cloudbox again

   - Remove Plex Container: `sudo docker rm -f plex` (it may show "Error response from daemon: No such container" if not created yet)

   - Remove the Plex folder: `sudo rm -rf /opt/plex`. 

   - Redo the [[installation|Installing Cloudbox]]. 


 - Using SSH Tunneling to log into Plex and set your credentials

   - On your host PC (replace with your user name and serveripaddress): `ssh <user>@<yourserveripaddress> -L 32400:0.0.0.0:32400 -N`

   - Go to http://localhost:32400/web.

   - Log in with your Plex account.

   - On the "How Plex Works" page, click “GOT IT!”. 

   - Close the "Plex Pass" pop-up if you see it.

   - Under "Server Setup", you will see "Great, we found a server!". Give your server a name and tick “Allow me to access my media outside my home”. Click "NEXT". 

   - On "Organize Your Media", hit "NEXT" (you will do this later). Then hit "DONE". 

   - At this point, you may `Ctrl + c` on the SSH Tunnel to close it. 




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

Reference: See https://unix.stackexchange.com/a/100887


## If during the first time setup, you switched the order of Plex libraries (i.e TV first then Movies)

  You will need to get the Plex section IDs and replace them in the Plex Autoscan config:

  1. Get section IDs by running the command:  `/opt/plex_autoscan/scan.py sections`.

  2. Edit the Plex Autoscan config via `nano /opt/plex_autoscan/config/config.json` and switch the ID numbers to match the Section IDs from Step 1 (for a more detailed explanation on this, see [[this|Customizing-Plex-Libraries#3-retrieving-plex-library-section-ids]]).

  3. Restart Plex Autoscan: `sudo systemctl restart plex_autoscan`   

## PlexPy logs location:

  - If you are asked for the plex logs location, it is exactly `/logs`.

## Server RAM is being maxed out?

If your server has ≤ 16GB RAM, it's possible Plexdrive is maxing it out (you can check this via `htop`). Try lowering the max chunks used by Plexdrive:

  1. `sudo nano /etc/systemd/system/plexdrive.service`

  1. Modify the `--max-chunks=250` to `--max-chunks=100`.

  1. `Ctrl-x`, `y`, and `enter` to save.
 
  1. `sudo systemctl daemon-reload`

  1. `sudo systemctl restart plexdrive.service`


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

## During Cloudbox install, get the message "... 403 Client Error: Forbidden: ... endpoint with name \<container name\> already exists in network \<network name\>":

Example:

```
fatal: [localhost]: FAILED! => {"changed": false, "failed": true, "msg": "Error starting container 6fb60d4cdabe938986042e06ef482012a1d85a66a099d861f08062d8262c2ef7: 403 Client Error: Forbidden (\"{\"message\":\"endpoint with name jackett already exists in network bridge\"}\")"}
    to retry, use: --limit @/home/seed/cloudbox/cloudbox.retry
PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=1  
```

You have a remnant of the container in the Docker's network. 

You can verify with the command below (replace `<network name>` and `<container name>` is replaced with the network name and container name mentioned in the error, respectively):
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

   To fix this, Run the following (replace `seed` with your user:group):

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




## Don't see your Google Drive files in /mnt/plexdrive?

### Check on status

```
sudo systemctl status plexdrive
```

### Error: `Process: XXXXX ExecStop=/bin/fusermount -uz /mnt/plexdrive (code=exited, status=217/USER)`

This could happen if you already had a user account on the server before adding it to settings.yml. 

You simply need to edit 3 files located in `/etc/systemd/system/` (`plex_autoscan.service`, `plexdrive.service`, and `unionfs.service`) like this...
```
sudo nano /etc/systemd/system/plexdrive.service
```

and change `User` and `Group` under `[Service]` to match yours' (run `id` on command prompt to check):

```
[Service]
User=yourusername
Group=yourgroupname
```

After editing all three files, reload systemctl:

```
sudo systemctl daemon-reload
```

And restart the services:

```
sudo systemctl restart plexdrive.service
sudo systemctl restart unionfs.service
sudo systemctl restart plex_autoscan.service
```


## How to fix permission issues:


## /opt folder

1. Stop all docker containers

   ```
   docker stop $(docker ps -a -q)
   ```

1. Change ownership of /opt. Replace `user` and `group` to match yours' (run `id` on command prompt to check).

   ```
   sudo chown -R user:group /opt
   ```

1. Change permission inheritance of /opt. 

   ```
   sudo chmod -R g+s /opt
   ```

1. Start all docker containers

   ```
   docker start $(docker ps -a -q)
   ```


## /mnt folder


1. Stop all docker containers

   ```
   docker stop $(docker ps -a -q)
   ```

1. Stop Unionfs and Plexdrive

   ```
   sudo systemctl stop unionfs.service
   sudo systemctl stop plexdrive.service
   ```


1. Change ownership of /mnt. Replace `user` and `group` to match yours' (run `id` on command prompt to check).

   ```
   sudo chown -R user:group /mnt
   ```


1. Change permission inheritance of /mnt. 

   ```
   sudo chmod -R g+s /mnt
   ```



1. Start Unionfs and Plexdrive

   ```
   sudo systemctl start unionfs.service
   sudo systemctl start plexdrive.service
   ```


1. Start all docker containers

   ```
   docker start $(docker ps -a -q)
   ```


## Temporary fix for Radarr not working with Plex Autoscan

Update: This has been fixed in newer versions of Radarr and Plex Autoscan. To update them, see [[Updating Cloudbox Apps]]. 


~~Currently, Radarr broke the webhook feature that allows Plex Autoscan to work properly. We've created a workaround to get it working until Radarr fixes it.~~ 

~~1. First, we will temporarily disable the Plex Autoscan connection: Radarr -> Settings -> Connect -> Plex Autoscan -> set all options to `No` -> click "Save".~~   

~~1. Create a new custom script: '+' -> Custom Script.~~

~~1. Add the following:~~

   ~~1. Name: Plex Autoscan fix~~

   ~~1. On Grab: `No`~~

   ~~1. On Download: `Yes`~~

   ~~1. On Upgrade:  `Yes`~~

   ~~1. On Rename:`No`~~

   ~~1. Path: `/scripts/plex_autoscan/radarr2autoscan.sh`~~


~~1. The settings will look like this:~~
 
~~https://i.imgur.com/KZOu3zD.png~~

~~1. Click "Save".~~




## If you cloned the script as USER_X but install as USER_Y 

You must move the cloudbox folder to USER_Y's home folder after installation completes.

Steps to run as USER_Y: 

```
cp /home/USER_X/cloudbox /home/USER_Y -R
sudo rm -rf /home/USER_X/cloudbox
```

## To change your ruTorrent password after installation


You may do this 2 ways:

- Reinstall the ruTorrent container

  * Stop and remove the container: `docker stop rutorrent && docker rm rutorrent`

  * Edit the settings.yml file with the new password: see [[Configuring Settings]]
  * Install the new ruTorrent container: `cd ~/ && sudo ansible-playbook cloudbox.yml --tags update-rutorrent`

- Change the password for the current ruTorrent container

  * Stop the container: `docker stop rutorrent`

  * Go into the folder where .htpasswd resides: `cd /opt/rutorrent/nginx`
  * Rename the old .htpasswd: `mv .htpasswd .htpasswd.bak`
  * Generate a new .htpasswd (where `USER` is your username and `PASSWORD` is the new password): `printf "USER:$(openssl passwd -1 PASSWORD)\n" >> .htpasswd`
  * And verify that `/opt/rutorrent/nginx/nginx.conf` has `auth_basic "Restricted Content";` and `auth_basic_user_file /config/nginx/.htpasswd;` inside all location references. See image below.
  * ![  ](https://i.imgur.com/VyyijSP.png)
  * Start the container: `docker start rutorrent`


## If you are importing your previous Sonarr and Radarr database..

Cloudbox uses Sonarr's develop branch and Radarr's nightly branch during install. If you want to import an existing database that is on Sonarr's master branch or Radarr's develop branch (the two most stable branches), you should upgrade to those releases on a working installation first, make a backup, and then import into the respective folders (i.e. `/opt/sonarr/` or `/opt/radarr/`).


## If Plex shows you an incorrect title with the filename (e.g. with -RARBG).

Reorder the Plex agents for TV/Movies so that local assets are at the bottom.

## Fix permission issues with Plex logs 


Run this command. Replace `seed:seed` with your user:group (`id` command).
```
sudo chown -R seed:seed /opt/plex/Library/Logs
```

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._
 

## Plex Autoscan log shows error during empty trash request

```
ERROR - PLEX [10490]: Unexpected response status_code for empty trash request: 401
```

You need to generate another token and re-add that back into the config. See [[Plex Autoscan]].



## Rclone error: Failed to save config file: open /home/<user>/.config/rclone/rclone.conf: permission denied

Replace `user` and `group` to match yours' (run `id` on command prompt to check)

```
sudo chown -R user:group /opt/rclone
sudo chmod -R 0755 /opt/rclone 
```


## Missing Thumbnails in Plex (due to http/https redirect errors)

_A recent update to Plex AND/OR nginx-proxy has resulted in an issue where Plex decides to try and load item posters from http via port 443. This behavior is limited to Android clients, as iOS and Web clients work perfectly fine. It is unsure which piece of software is at fault here, be it nginx-proxy or most likely Plex. However, a temporary fix is provided below._



1. Go into the folder:

   ```
   cd ~/cloudbox
   ```
1. Edit the nginx-role
   ```
   nano roles/nginx-proxy/tasks/main.yml
   ```

1. Change `image:` info

   Replace ...
   ```    
   image: "jwilder/nginx-proxy" 
   ```

   With ...
   ```    
   image: "jwilder/nginx-proxy@sha256:76d9ed11c131fadc7546e3b9b085970e13ff45186171b975ad60830f5ca0d689" 
   ```

1. Save the file: `Ctrl-X` + `Y`.

1. Recreate the nginx-proxy container
 
   ```    
   sudo ansible-playbook cloudbox.yml --tags update-nginx
   ```



## Plex Autoscan error with metadata_item_id

Example Log:
```
 2017-11-21 04:26:32,619 -    ERROR -      PLEX [ 7089]: Exception finding metadata_item_id for '/data/TV/Gotham/Season 01/Gotham - S01E01 - Pilot.mkv': 

Traceback (most recent call last):

  File "/opt/plex_autoscan/plex.py", line 208, in get_file_metadata_id

    media_item_id = c.execute("SELECT * FROM media_parts WHERE file=?", (file_path,)).fetchone()[1]

TypeError: 'NoneType' object has no attribute '__getitem__'

 2017-11-21 04:26:32,619 -     INFO -      PLEX [ 7089]: Aborting analyze of '/data/TV/Gotham/Season 01/Gotham - S01E01 - Pilot.mkv' because could not find a metadata_item_id for it
```


Issue: 

One of the mounts has changed (e.g. Plexdrive or UnionFS was restarted).

Fix:

1. Make sure Plexdrive and Unionfs are working ok 
   ```
   sudo systemctl status plexdrive
   ```
   ```
   sudo systemctl status unionfs
   ```

1. Restart Plex:
   ```
   docker stop plex && docker start plex
   ```

## Purpose of a Control File in Plex Autoscan

The control file is a blank file (i.e. `mounted.bin`) that resides on the root folder of Google Drive. The purpose of a control file is to tell Plex Autoscan that your Google Drive is mounted.

If Plex scanned for media when the Google Drive mount was ever disconnected, it would mark the missing files as "unavailable", and would wait on an emptying trash request to remove them completely. Plex Autoscan, however, would not send that request since the control file would not be available. Once Google Drive was remounted, all the files marked unavailable in Plex would be playable again and Plex Autoscan would resume its emptying trash duties post-scan.

To learn more about Plex Autoscan, see https://github.com/l3uddz/plex_autoscan.
