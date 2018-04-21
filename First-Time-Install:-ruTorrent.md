ruTorrent is a front-end for the popular BitTorrent client rtorrent, it's lightweight and extensible. 


## 1. Accessing ruTorrent

- To access ruTorrent, visit https://rutorrent._yourdomain.com_

## 2. Basics

ruTorrent comes setup out of the box with the login settings (username and ruTorrent password) you set in [[settings.yml|first-time-install: configuring-settings]].

  - _Note: If you need to change the password after installing Cloudbox, see the [[FAQ#to-change-your-rutorrent-password-after-installation]]._

The setup for Sonarr and Radarr are done on their respective wiki pages (i.e. [[Sonarr#ruTorrent|First-Time-Install:-Sonarr#rutorrent]] and [[Radarr#ruTorrent|First-Time-Install:-Radarr#rutorrent]]).

## 3. Enable AutoUnpack

AutoUnpack is a plugin that will automatically unrar/unzip torrent data. 

_This will allow Sonarr and Radarr to import the media files that would otherwise be ignored. After Sonarr and Radarr import the media files, [[Torrent Cleanup Script|Cloudbox-Tools#torrent-cleanup-script]] will then delete the extracted media files and ruTorrent will continue to seed the torrents (until they are either removed manually or automatically via ruTorrent's Ratio Group rules)._

To enable AutoUnpack:

1. Open "Settings" by clicking the gear icon ![](https://github.com/Novik/ruTorrent/wiki/images/icon06settings.png) at the top

1. Go to "Unpack" on the left. 

1. Check "Enable autounpacking if torrents label matches filter": `/.*/`

1. Leave the other fields blank. 

1. Click "OK". 

 ![](https://i.imgur.com/YzkJRyf.png)