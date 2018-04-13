<!-- TOC depthFrom:1 depthTo:2 withLinks:1 updateOnSave:1 orderedList:0 -->

- [System](#system)
	- [Can I install this on an ARM machine?](#can-i-install-this-on-an-arm-machine)
	- [If you are using a Scaleway server...](#if-you-are-using-a-scaleway-server)
	- [If you are using an OVH server...](#if-you-are-using-an-ovh-server)
	- [Server RAM is being maxed out](#server-ram-is-being-maxed-out)
	- [Find your User ID (UID) and Group ID (GID)](#find-your-user-id-uid-and-group-id-gid)
	- [Change shell of user account to bash](#change-shell-of-user-account-to-bash)
	- [How to fix permission issues](#how-to-fix-permission-issues)
- [Domain Name](#domain-name)
	- [Freenom email](#freenom-email)
- [Cloud Storage](#cloud-storage)
	- [Does Cloudbox support encryption data on Google Drive?](#does-cloudbox-support-encryption-data-on-google-drive)
	- [Why does Cloudbox not support encryption data on Google Drive?](#why-does-cloudbox-not-support-encryption-data-on-google-drive)
	- [Does Cloudbox support any other cloud storage provider other than Google Drive?](#does-cloudbox-support-any-other-cloud-storage-provider-other-than-google-drive)
- [Cloudbox Installer](#cloudbox-installer)
	- [If you cloned the script as USER1 but installed as USER2](#if-you-cloned-the-script-as-user1-but-installed-as-user2)
	- [Unrar module fails to install during the Common Role step](#unrar-module-fails-to-install-during-the-common-role-step)
	- [Misc SSL Errors During Install](#misc-ssl-errors-during-install)
	- [Error while fetching server API version](#error-while-fetching-server-api-version)
	- [403 Client Error: Forbidden: endpoint with name \<container name\> already exists in network \<network name\>](#403-client-error-forbidden-endpoint-with-name-container-name-already-exists-in-network-network-name)
	- [500 Server Error: Internal Server Error: driver failed programming external connectivity on endpoint \<container name\> bind for 0.0.0.0:\<port number\> failed: port is already allocated](#500-server-error-internal-server-error-driver-failed-programming-external-connectivity-on-endpoint-container-name-bind-for-0000port-number-failed-port-is-already-allocated)
	- [apt-get Gets Stuck at 0% Because of IPv6](#apt-get-gets-stuck-at-0-because-of-ipv6)
- [Docker](#docker)
	- [Why does Cloudbox use the Docker network "cloudbox" instead of bridge?](#why-does-cloudbox-use-the-docker-network-cloudbox-instead-of-bridge)
	- [Docker Commands Hang](#docker-commands-hang)
- [Nginx Proxy](#nginx-proxy)
	- [SSL Certificate Issues](#ssl-certificate-issues)
	- [Cloudbox app subdomains redirect elsewhere (eg. sonarr.domain.com goes to NZBGet)](#cloudbox-app-subdomains-redirect-elsewhere-eg-sonarrdomaincom-goes-to-nzbget)
	- [Too many certificates already issued for domain.com](#too-many-certificates-already-issued-for-domaincom)
	- [CA marked some of the authorizations as invalid](#ca-marked-some-of-the-authorizations-as-invalid)
	- [Error 502](#error-502)
- [Rclone](#rclone)
	- [Rclone error: Failed to save config file: open /home/\<user\>/.config/rclone/rclone.conf: permission denied](#rclone-error-failed-to-save-config-file-open-homeuserconfigrclonercloneconf-permission-denied)
- [Plexdrive](#plexdrive)
	- [Don't see your Google Drive files in /mnt/plexdrive?](#dont-see-your-google-drive-files-in-mntplexdrive)
- [Plex](#plex)
	- [If you are unable to find your Plex server](#if-you-are-unable-to-find-your-plex-server)
	- [If Plex shows you an incorrect title with the filename (eg RARBG releases)](#if-plex-shows-you-an-incorrect-title-with-the-filename-eg-rarbg-releases)
	- [Fix permission issues with Plex logs](#fix-permission-issues-with-plex-logs)
	- [Missing Thumbnails in Plex (due to http/https redirect errors)](#missing-thumbnails-in-plex-due-to-httphttps-redirect-errors)
	- [Update WebTools](#update-webtools)
- [Plex Autoscan](#plex-autoscan)
	- [If during the first time setup, you switched the order of Plex libraries (i.e TV first then Movies)](#if-during-the-first-time-setup-you-switched-the-order-of-plex-libraries-ie-tv-first-then-movies)
	- [Newly downloaded media from Sonarr and Radarr are not being added to Plex?](#newly-downloaded-media-from-sonarr-and-radarr-are-not-being-added-to-plex)
	- [Plex Autoscan log shows error during empty trash request](#plex-autoscan-log-shows-error-during-empty-trash-request)
	- [Plex Autoscan error with metadata item id](#plex-autoscan-error-with-metadata-item-id)
	- [Purpose of a Control File in Plex Autoscan](#purpose-of-a-control-file-in-plex-autoscan)
- [UnionFS Cleaner](#unionfs-cleaner)
- [Sonarr and Radarr](#sonarr-and-radarr)
	- [If you are importing your previous Sonarr and Radarr database..](#if-you-are-importing-your-previous-sonarr-and-radarr-database)
- [ruTorrent](#rutorrent)
	- [To change your ruTorrent password after installation](#to-change-your-rutorrent-password-after-installation)
- [Nextcloud](#nextcloud)
	- [Backup/Restore DB](#backuprestore-db)


<!-- /TOC -->


---

# System



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

1. You can skip [[updating the kernel|First Time Install: Updating Kernel]].

Reference: https://www.scaleway.com/docs/bootscript-and-how-to-use-it/


## If you are using an OVH server...

If you are having issues upgrading the kernel on ovh, where the kernel upgrade is not taking effect..

 `uname -r` to see if you have `grs` in kernel version string...

 if so, see https://pterodactyl-daemon.readme.io/v0.4/docs/updating-ovh-kernel on how to update the kernel.



## Server RAM is being maxed out

If your server has < 16GB RAM, it's possible Plexdrive is maxing it out (you can check this via `htop`). Try lowering the max chunks used by Plexdrive:

  1. `sudo nano /etc/systemd/system/plexdrive.service`

  1. Modify the `--max-chunks=250` to something lower (e.g. `--max-chunks=100`).

  1. `Ctrl-x`, `y`, and `enter` to save.

  1. `sudo systemctl daemon-reload`

  1. `sudo systemctl restart plexdrive.service`




## Find your User ID (UID) and Group ID (GID)

Use the following commands to find out your account's user name and group info:

```
id
```
or

```
id `whoami`
```




You'll see a line like the following:

```
uid=1000(yourusername) gid=1001(yourgroup) groups=1001(yourgroup)
```



## Change shell of user account to bash

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





## How to fix permission issues


### /opt folder

1. Stop all docker containers

   ```
   docker stop $(docker ps -a -q)
   ```

1. Change ownership of /opt. Replace `user` and `group` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid)).

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


### /mnt folder


1. Stop all docker containers

   ```
   docker stop $(docker ps -a -q)
   ```

1. Stop Unionfs and Plexdrive

   ```
   sudo systemctl stop unionfs.service
   sudo systemctl stop plexdrive.service
   ```


1. Change ownership of /mnt. Replace `user` and `group` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid)).

   ```
   sudo chown -R user:group /mnt
   ```


1. Change permission inheritance of /mnt.

   ```
   sudo chmod -R g+s /mnt
   ```



1. Start Unionfs and Plexdrive

   ```
   sudo systemctl start plexdrive.service
   sudo systemctl start unionfs.service
   ```


1. Start all docker containers

   ```
   docker start $(docker ps -a -q)
   ```





# Domain Name



## Freenom email


```Dear ------,

The Freenom Review Team has visited your website today.
Your domain: ------
We found that the free domain name and/or the website address you used
with your free domain name was not accessible or did not follow the
guidelines set in our terms and conditions.

It may well be that you are still working on the content of your website
and/or using your domain for other means. We kindly request to start using
your new domain soon according to the terms and conditions which can be found at:
http://www.freenom.com/en/termsandconditions.html

In a few days from now we will visit your website again. To prevent domain
hijacking all domains that are not accessible or not follow the guidelines
set in our terms and conditions will be cancelled.
```

If you get a domain from Freenom and don't actually set it up, you'll get this email. If you want to stop getting them, then you should look into getting a paid [[domain| Basics: Prerequisites#i-paid-domain-name-recommended]].








# Cloud Storage


## Does Cloudbox support encryption data on Google Drive?

In short, no.

## Why does Cloudbox not support encryption data on Google Drive?

While there are pro's and cons for using either encrypted or unencrypted data on cloud services, Cloudbox developer(s) have decided to not support encrypted cloud data.

Note: You may be able to modify Cloudbox to use encrypted data stored on the cloud (see [here](https://github.com/dweidenfeld/plexdrive/blob/master/TUTORIAL.md)), but that will be on you to setup yourself with no support from us.

## Does Cloudbox support any other cloud storage provider other than Google Drive?

In short, no.

Note: You may be able to modify Cloudbox to use another cloud storage provider (see [here](https://rclone.org/commands/rclone_mount/)), but that will be on you to setup yourself with no support from us.


# Cloudbox Installer


## If you cloned the script as USER1 but installed as USER2

You must move the `cloudbox` folder to USER2's home folder after installation completes.

Steps to run as USER2:

```
cp -R /home/USER1/cloudbox /home/USER2
sudo rm -rf /home/USER1/cloudbox
```


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


## Misc SSL Errors during Install

Example:
```
An exception occurred during task execution. To see the full traceback, use -vvv. The error was: AttributeError: 'module' object has no attribute 'Cryptography_HAS_SSL_ST'
```

This seems to occur on certain VM systems.

To fix it the issue, run the following command:

```
sudo easy_install pyOpenSSL

```

Rerun the [Install Dependencies](First-Time-Install%3A-Downloading-Cloudbox#1-install-dependencies) command and retry Cloudbox Install..


## Error while fetching server API version

Full error message:

```
Error Connecting:  Error while fetching server API version: Timeout value connect was Timeout(connect=60, read=60, total=None), but it must be an int or float.
```


Run `sudo pip install requests==2.10.0` and retry.




## 403 Client Error: Forbidden: endpoint with name \<container name\> already exists in network \<network name\>

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


## 500 Server Error: Internal Server Error: driver failed programming external connectivity on endpoint \<container name\> bind for 0.0.0.0:\<port number\> failed: port is already allocated

```
sudo service docker stop
sudo service docker start
```




## apt-get Gets Stuck at 0% Because of IPv6

Example:
```
Get:65 http://mirror.hetzner.de/ubuntu/packages xenial-updates/multiverse amd64 Packages [16.2 kB]
Get:66 http://mirror.hetzner.de/ubuntu/packages xenial-updates/multiverse i386 Packages [15.3 kB]
Get:67 http://mirror.hetzner.de/ubuntu/packages xenial-updates/multiverse Translation-en [8,076 B]
Get:68 http://mirror.hetzner.de/ubuntu/security xenial-security/main amd64 Packages [472 kB]
Get:69 http://mirror.hetzner.de/ubuntu/security xenial-security/main i386 Packages [424 kB]
Get:70 http://mirror.hetzner.de/ubuntu/security xenial-security/main Translation-en [204 kB]
Get:71 http://mirror.hetzner.de/ubuntu/security xenial-security/restricted amd64 Packages [7,224 B]
Get:72 http://mirror.hetzner.de/ubuntu/security xenial-security/restricted i386 Packages [7,224 B]
Get:73 http://mirror.hetzner.de/ubuntu/security xenial-security/restricted Translation-en [2,152 B]
Get:74 http://mirror.hetzner.de/ubuntu/security xenial-security/universe amd64 Packages [340 kB]
Get:75 http://mirror.hetzner.de/ubuntu/security xenial-security/universe i386 Packages [297 kB]
Get:76 http://mirror.hetzner.de/ubuntu/security xenial-security/universe Translation-en [127 kB]
Get:77 http://mirror.hetzner.de/ubuntu/security xenial-security/multiverse amd64 Packages [3,208 B]
Get:78 http://mirror.hetzner.de/ubuntu/security xenial-security/multiverse i386 Packages [3,376 B]
Get:79 http://mirror.hetzner.de/ubuntu/security xenial-security/multiverse Translation-en [1,408 B]
0% [Connecting to security.ubuntu.com (2001:67c:1360:8001::21)]
```

Run this command:
``` bash
echo 'Acquire::ForceIPv4 "true";' | sudo tee /etc/apt/apt.conf.d/99force-ipv4
```

Retry install.



# Docker


## Why does Cloudbox use the Docker network "cloudbox" instead of bridge?

(1) keeps all Cloudbox containers organized under one network; and (2), bridge network does not allow network aliases.


## Docker Commands Hang


Issue: Docker apps stop loading and/or docker commands (e.g. `docker --version`) hang.

One reason this can happen is if docker-ce was recently updated.

To fix this:

Stop the service first

```
sudo service docker stop
```

Clean up some of the files as mentioned in above post from Sam.


```
sudo rm -rf /var/run/docker
sudo rm /var/run/docker.*
```

Start service now

```
sudo service docker start
```

Start your docker image

```
docker start <container-name>
```


---


You might receive an error when you run the docker run at first try:

```
Error response from daemon: invalid header field value "oci runtime error: container with id exists: 7a244b8f5d07081538042ff64aebfe11fac1a36731526e77be53db7d94dca44d\n"
Error: failed to start containers:
```

Try running docker start command again. You will have your container up and running magically without any errors.




source: https://forums.docker.com/t/what-to-do-when-all-docker-commands-hang/28103/5

# Nginx Proxy



## SSL Certificate Issues


You can view the status via looking at the [[log|Logs#docker-logs]] for the `letsencrypt` container.

```
docker logs -f letsencrypt
```

And see if the issues below apply to you..


## Cloudbox app subdomains redirect elsewhere (eg. sonarr.domain.com goes to NZBGet)

This happens when SSL certificates have not been issued yet.

You may even see `too many registrations for this IP` in the log (like below)...

```
2017-11-30 03:35:41,847:INFO:simp_le:1538: Retrieving Let's Encrypt latest Terms of Service.
2017-11-30 03:35:42,817:INFO:simp_le:1356: Generating new account key
ACME server returned an error: urn:acme:error:rateLimited :: There were too many requests of a given type :: Error creating new registration :: too many registrations for this IP
```

Just give it some time (days to hours) and it will resolve itself.



## Too many certificates already issued for domain.com

```
Creating/renewal request.domain.com certificates... (request.domain.com)
2017-12-02 07:34:44,167:INFO:simp_le:1538: Retrieving Let's Encrypt latest Terms of Service.
2017-12-02 07:34:45,331:INFO:simp_le:1356: Generating new account key
2017-12-02 07:34:46,853:INFO:simp_le:1455: Generating new certificate private key
ACME server returned an error: urn:acme:error:rateLimited :: There were too many requests of a given type :: Error creating new cert :: too many certificates already issued for: domain.com
```


You're limited to 20 new certificates, per registered domain, per week.

See https://letsencrypt.org/docs/rate-limits/ for more info.


## CA marked some of the authorizations as invalid


```
2017-11-30 03:35:37,729:INFO:simp_le:1538: Retrieving Let's Encrypt latest Terms of Service.
2017-11-30 03:35:40,256:INFO:simp_le:1455: Generating new certificate private key
2017-11-30 03:35:41,406:ERROR:simp_le:1421: CA marked some of the authorizations as invalid, which likely means it could not access http://example.com/.well-known/acme-challenge/X. Did you set correct path in -d example.com:path or --default_root? Are all your domains accessible from the internet? Please check your domains' DNS entries, your host's network/firewall setup and your webserver config. If a domain's DNS entry has both A and AAAA fields set up, some CAs such as Let's Encrypt will perform the challenge validation over IPv6. If you haven't setup correct CAA fields or if your DNS provider does not support CAA, validation attempts after september 8, 2017 will fail.  Failing authorizations: https://acme-v01.api.letsencrypt.org/acme/authz/XXXXXXXXXX
Challenge validation has failed, see error log.
```

- Make sure your [[domain registrar| Basics: Prerequisites#3-domain-name]] is pointing to the correct server IP address. You can verify this by pinging it (`ping yourdomain.com`).

- Make sure you used the correct domain address in [[settings.yml|First Time Install: Configuring Settings]].



## Error 502

Due to a recent change with the Suitarr image, the ports for the five Suitarr containers (i.e. Sonarr, Radarr, Jackett, NZBGet, and NZBHydra) have also changed.

If your docker images haven't been updated yet, you can preemptively avoid any Error 502 issues by going in to each of these apps settings pages and changing the ports to 8989, 7878, 9117, 6789, 5075, respectively, and then update all five of these docker containers with the --tags update-xxxxx command (see [here](Updating-Cloudbox-Apps#rebuild-the-docker-containers)).

If the Suitarr docker image has been updated (e.g. Cloudbox update) and now you are getting Error 502s, you will need to edit the config files in the /opt/ folder and manually put in these ports. 

1. `/opt/sonarr/config.xml`

   ```
   <Port>8989</Port>
   ``` 


1. `/opt/radarr/config.xml` 

   ```
   <Port>7878</Port>
   ```


1. `/opt/jackett/Jackett/ServerConfig.json`

   ```
   "Port": 9117,
   ```


1. `/opt/nzbget/nzbget.conf `

   ```
   ControlPort=6789
   ```

1. `/opt/nzbhydra/nzbhydra.cfg` 

   Under:
   ```
   "main" {
   ```

   Edit:
   ```
   "port": 5075,
   ```

1. After the above edits, restart the docker containers: 

   ```
   docker restart sonarr radarr jackett nzbget nzbhydra
   ```

1. The apps above will now load OK, however, you will still to edit the ports within the app settings:
 
   1. Jackett, NZBGet, and NZBHydra in Sonarr/Radarr settings.

   1. NZBGet port in NZBHydra settings.

   1. Radarr and Sonarr ports in Plex Requests settings.

   1. Radarr, Sonarr, and NZBGet in Organizr settings.



# Rclone



## Rclone error: Failed to save config file: open /home/\<user\>/.config/rclone/rclone.conf: permission denied

Replace `user` and `group` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid)).

```
sudo chown -R user:group /opt/rclone
sudo chmod -R 0755 /opt/rclone

```

```
sudo chown -R user:group ~/.config/rclone/
sudo chmod -R 0755 ~/.config/rclone/
```



# Plexdrive



## Don't see your Google Drive files in /mnt/plexdrive?


### Make sure your files are in the correct Google Drive paths.


See [[Basics: Paths]] and [[Basics: Prerequisites#4-google-drive-account]]. Remember folder names mentioned throughout the site are **CASE SENSITIVE**.


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

Replace `User` and `Group` under  `[Service]` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid)).

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





# Plex



## If you are unable to find your Plex server

You may resolve this by either

 - Installing Cloudbox again

   - Remove Plex Container (it may show "Error response from daemon: No such container" if not created yet):

     ```
     sudo docker rm -f plex
     ```

   - Remove the Plex folder:

     ```
     sudo rm -rf /opt/plex
     ```

   - Reinstall the Plex container by running the following command in `~/cloudbox`:

     ```
     sudo ansible-playbook cloudbox.yml --tags update-plex
     ```


 - Using SSH Tunneling to log into Plex and set your credentials

   - On your host PC (replace `<user>` with your user name and `<yourserveripaddress>` with your serveripaddress - no arrows):

     ```
     ssh <user>@<yourserveripaddress> -L 32400:0.0.0.0:32400 -N
     ```

     This will just hang there without any message. That is normal.

   - In a browser, go to http://localhost:32400/web.

   - Log in with your Plex account.

   - On the "How Plex Works" page, click “GOT IT!”.

   - Close the "Plex Pass" pop-up if you see it.

   - Under "Server Setup", you will see "Great, we found a server!". Give your server a name and tick “Allow me to access my media outside my home”. Click "NEXT".

   - On "Organize Your Media", hit "NEXT" (you will do this later). Then hit "DONE".

   - At this point, you may `Ctrl + c` on the SSH Tunnel to close it.



## If Plex shows you an incorrect title with the filename (eg RARBG releases)

Reorder the Plex agents for TV/Movies so that local assets are at the bottom.




## Fix permission issues with Plex logs


Replace `user` and `group` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid)).

```
sudo chown -R user:group /opt/plex/Library/Logs
sudo chmod -R g+s /opt/plex/Library/Logs
```

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._






## Missing Thumbnails in Plex (due to http/https redirect errors)

**Update:** This has been added to Cloudbox as default config. Just [[update Cloudbox|Updating Cloudbox]] and [[reinstall nginx proxy|Updating Cloudbox Apps]]

~~_A recent update to Plex AND/OR nginx-proxy has resulted in an issue where Plex decides to try and load item posters from http via port 443. This behavior is limited to Android clients, as iOS and Web clients work perfectly fine. It is unsure which piece of software is at fault here, be it nginx-proxy or most likely Plex. However, a temporary fix is provided below._~~



~~1. Go into the folder:~~

   ```
   cd ~/cloudbox
   ```
~~1. Edit the nginx-role~~
   ```
   nano roles/nginx-proxy/tasks/main.yml
   ```

~~1. Change `image:` info~~

  ~~ Replace ...~~
   ```    
   image: "jwilder/nginx-proxy"
   ```

   ~~With ...~~
   ```    
   image: "jwilder/nginx-proxy@sha256:76d9ed11c131fadc7546e3b9b085970e13ff45186171b975ad60830f5ca0d689"
   ```

~~1. Save the file: `Ctrl-X` + `Y`.~~

~~1. Recreate the nginx-proxy container~~

   ```    
   sudo ansible-playbook cloudbox.yml --tags update-nginx
   ```

## Update WebTools

1. Remove your current WebTools.bundle folder.

   ```
   rm -rf "/opt/plex/Library/Application Support/Plex Media Server/Plug-ins/WebTools.bundle"
   ```

2. Update the Plex container

   ```
   cd ~/cloudbox
   sudo ansible-playbook cloudbox.yml --tags update-plex
   ```

3. Access Webtools

   ```
   http://plex.yourdomain.com:33400 (or http://youripaddress:33400)
   ```





# Plex Autoscan

## If during the first time setup, you switched the order of Plex libraries (i.e TV first then Movies)

  You will need to get the Plex section IDs and replace them in the Plex Autoscan config:

  1. Get section IDs by running the command:  `/opt/plex_autoscan/scan.py sections`.

  2. Edit the Plex Autoscan config via `nano /opt/plex_autoscan/config/config.json` and switch the ID numbers to match the Section IDs from Step 1 (for a more detailed explanation on this, see [[this|Customizing-Plex-Libraries#3-retrieving-plex-library-section-ids]]).

  3. Restart Plex Autoscan: `sudo systemctl restart plex_autoscan`   



## Newly downloaded media from Sonarr and Radarr are not being added to Plex?

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

   To fix this, Run the following command. Replace `user` and `group` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid)).

   ```
   docker stop plex
   sudo chown -R user:group /opt/plex
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


## Plex Autoscan log shows error during empty trash request

```
ERROR - PLEX [10490]: Unexpected response status_code for empty trash request: 401
```

You need to generate another token and re-add that back into the config. See [[Plex Autoscan | First-Time-Install: Plex Autoscan]].



## Plex Autoscan error with metadata item id

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

Every time Sonarr or Radarr downloads a new file, or upgrades a previous one, a request is sent to Plex via Plex Autoscan to scan the movie folder or TV season path and look for changes. Since Sonarr and Radarr delete previous files on upgrades, the scan will cause the new media to show up in your Plex Library, however, the deleted files would be missing, and instead, marked as "unavailable" (i.e. trash icon). When the control file is present and the option in the Plex Autoscan config is enabled (default), Plex Autoscan will empty the trash for you, thereby, removing the deleted media from the library.

If your Google Drive ever disconnected during a Plex scan of your media, Plex would mark the missing files as unavailable and emptying the trash would cause them to be removed out of the library. To avoid this from happening, Plex Autoscan checks for a control file in the unionfs path (i.e. `/mnt/unionfs/mounted.bin)` before running any empty trash commands. The control file is just a blank file that resides on the root folder of Google Drive and let's Plex Autoscan know that your Google Drive is mounted.

Once Google Drive is remounted, all the files marked unavailable in Plex will be playable again and Plex Autoscan will resume its emptying trash duties post-scan.

To learn more about Plex Autoscan, see https://github.com/l3uddz/plex_autoscan.



# UnionFS Cleaner

See [[UnionFS Cleaner]].


# Sonarr and Radarr


## If you are importing your previous Sonarr and Radarr database..

Cloudbox uses Sonarr's develop branch and Radarr's nightly branch during install. If you want to import an existing database that is on Sonarr's master branch or Radarr's develop branch (the two most stable branches), you should upgrade to those releases on a working installation first, make a backup, and then import into the respective folders (i.e. `/opt/sonarr/` or `/opt/radarr/`).



# ruTorrent



## To change your ruTorrent password after installation


You may do this 2 ways:

- Reinstall the ruTorrent container

  * Stop and remove the container: `docker stop rutorrent && docker rm rutorrent`

  * Remove the ruTorrent folder: `sudo rm -rf /opt/rutorrent`

  * Edit the settings.yml file with the new password: see [[Configuring Settings | First Time Install: Configuring Settings]]

  * Install the new ruTorrent container: `cd ~/cloudbox && sudo ansible-playbook cloudbox.yml --tags update-rutorrent`

- Change the password for the current ruTorrent container

  * Stop the container: `docker stop rutorrent`

  * Go into the folder where .htpasswd resides: `cd /opt/rutorrent/nginx`

  * Rename the old .htpasswd: `mv .htpasswd .htpasswd.bak`

  * Generate a new .htpasswd (where `USER` is your username and `PASSWORD` is the new password): `printf "USER:$(openssl passwd -1 PASSWORD)\n" >> .htpasswd`

  * And verify that `/opt/rutorrent/nginx/nginx.conf` has `auth_basic "Restricted Content";` and `auth_basic_user_file /config/nginx/.htpasswd;` inside all location references. See image below.

  * ![  ](https://i.imgur.com/VyyijSP.png)

  * Start the container: `docker start rutorrent`


# Nextcloud



## Backup/Restore DB

DB data is stored in /opt/mariadb and backedup along with Cloudbox Backup. 

However, you can separately make a backup of the DB into a single `nextcloud_backup.sql` file, by running the following command. 

```
docker exec mariadb /usr/bin/mysqldump -u root --password=password321 nextcloud  > nextcloud_backup.sql

```

And restoring it back:

```
cat nextcloud_backup.sql | docker exec -i mariadb /usr/bin/mysql -u root --password=password321 nextcloud

```
