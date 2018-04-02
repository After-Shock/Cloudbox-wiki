## 1. Accessing Heimdall
* To access Heimdall, visit https://heimdall.yourdomain.com

## 2. Setup
There is nothing to do as far as getting Heimdall running. 

By default it is installed without a password, which may not be need by many users. However, if you would like to set a login you can do so with the following command.

`docker exec -it heimdall htpasswd -c /config/nginx/.htpasswd username`

Replacing _username_ with your desired name. Then you will be prompted for a password and once again to confirm.

## 3. Customizing
You are not limited to just the applications on your server with Heimdall. You can use it anything, such as a homepage with all your bookmarks and search engine.

### Adding Items
You can add items to Heimdall by clicking the _items_ tab follow by the _add_ button.

![](https://i.imgur.com/0c5jFEx.png)

![](https://i.imgur.com/3OLPW88.png)

Many of the applications that you may use have logos and hex colors filled in. You are able to change these if needed, however, not all of your applications will have these and you will have to do it manually.

![](https://i.imgur.com/pydRkW7.png)

In the picture above, you will see a spot to login at the bottom. This is not used for every application and some will require a API key to grant access. This allows you to have a quick glance at the service, pictured below.

![](https://i.imgur.com/1Mkwze1.png)

### Organizing
Clicking this _switch_ allows you reorganize your tabs. This is very helpful after adding a whole bunch, in no certain order.

![](https://i.imgur.com/mxNEvpp.png)

You now be able to drag and drop. You will also see a _pin_ tab, which will disappear when you exit out.

![](https://i.imgur.com/o9dB7us.png)

This allows you to add and remove items very fast, while saving them for later.

### Refreshing
If for any reason your tabs are not showing current information you can refresh with the _refresh_ button.

![](https://i.imgur.com/Ctm2nyq.png)

### Tags
Have a lot of stuff? Want to organize each service? The _tag_ system is pretty much a folder, where you can place items inside. You can also stack them on top of each other - _you have have a lot of stuff_.

![](https://i.imgur.com/hsLOlXk.png)

Just add a tag like you would a normal application. Then you can assign applications to the tag when setting up or editing them.

The tag is seen with a tag symbol on the right. 

![](https://i.imgur.com/gxtblyb.png)

### Settings
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