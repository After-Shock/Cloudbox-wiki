[Heimdall](https://heimdall.site/) is a dashboard for all your web applications and any other links you like to add. Can be set as your browser's start page, with the ability to include a search bar using either Google, Bing or DuckDuckGo. See [here](https://github.com/linuxserver/Heimdall#about) and [here](https://youtu.be/GXnnMAxPzMc) for a video preview. 

## 1. Accessing Heimdall

To access Heimdall, visit https://heimdall._yourdomain.com_


## 2. First Time Setup

### 1. Add Subdomain for Heimdall

See [[Adding a Subdomain | Extras: Adding a Subdomain]] on how to add the subdomain `heimdall` to your DNS provider.


### 2. Install Heimdall

Run the following commands: 

 ```bash
 cd ~/cloudbox/
 sudo ansible-playbook cloudbox.yml --tags install-heimdall  
 ```

### 3. Add Password

By default, Heimdall is installed without a password. 

To set up a login, run the following command:

```
docker exec -it heimdall htpasswd -c /config/nginx/.htpasswd username
```

Replacing _username_ with your desired name. You will then be prompted for a password. 

## 3. Customizing

You are not limited to just the applications on your server with Heimdall. You can use it for anything, including  all your bookmarks and your favorite search engine.

### 1. Adding Items

1. You can add items to Heimdall by clicking the _items_ tab follow by the _add_ button.

   ![](https://i.imgur.com/0c5jFEx.png)

   ![](https://i.imgur.com/3OLPW88.png)

2. Many of the applications that you may use have logos and hex colors filled in. You are able to change these if needed, however, not all of your applications will have these and you will have to do it manually.

   ![](https://i.imgur.com/pydRkW7.png)

3. In the picture above, you will see a spot to login at the bottom. This is not used for every application as some will require just an API key. This allows you to have a quick glance at the service, pictured below.

   ![](https://i.imgur.com/1Mkwze1.png)

### 2. Organizing

1. Clicking this _switch_ allows you reorganize your tabs. This is very helpful after adding a whole bunch, in no certain order.

   ![](https://i.imgur.com/mxNEvpp.png)

2. You now be able to drag and drop. You will also see a _pin_ tab, which will disappear when you exit out.

   ![](https://i.imgur.com/o9dB7us.png)

3. This allows you to add and remove items very fast, while saving them for later.

4. If for any reason your tabs are not showing current information you can refresh with the _refresh_ button.

   ![](https://i.imgur.com/Ctm2nyq.png)

### 4. Tags

Have a lot of stuff? Want to organize each service? The _tags_ work much like a folder, where you can place items inside. You can even stack them on top of each other. 


1. Just add a tag like you would a normal application. Then you can assign applications to the tag when setting up or editing them.

   ![](https://i.imgur.com/hsLOlXk.png)

2. The tag is seen with a tag symbol on the right. 

   ![](https://i.imgur.com/gxtblyb.png)

### 5. Settings

In the _settings_ menu you can find the options to update, change the background, and even add a search engine to it.

  ![](https://i.imgur.com/tFyp4Br.png)

  ![](https://i.imgur.com/C7hLmrd.png)

## 4. Supported Applications
You can add your own applications to Heimdall, but below are the predefined ones. There are two different types. _Foundation_ apps are your basic applications without any api access. _Enhanced_ apps can have additional information to provide a quick glance at them.

**Enhanced**
* Couchpotato
* Tautulli
* Pihole
* Sabnzbd
* NZBGet
* RuneAudio

**Foundation**
* Watcher
* OpenMediaVault
* Krusader
* Airsonic
* Glances
* Dokuwiki
* SickRage
* Gitea
* Ombi
* TT-RSS
* Graylog
* NZBHydra
* NZBHydra2
* Medusa
* Deluge
* rTorrent/ruTorrent
* OPNSense
* Netdata
* Lidarr
* Sonarr
* Radarr
* pFsense
* UniFI
* Portainer
* Plex
* Emby
* Duplicati
* JDownloader
* openHAB
* McMyAdmin
* Plexrequests
* Traefik
* Nextcloud