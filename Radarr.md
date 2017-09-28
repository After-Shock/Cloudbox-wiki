<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:0 -->

1. [Accessing Radarr](#1-accessing-radarr)
2. [General Settings](#2-general-settings)
3. [Media Management](#3-media-management)
4. [Download Clients](#4-download-clients)
	- [NZBGet](#nzbget)
	- [ruTorrent](#rutorrent)
5. [Indexers](#5-indexers)
	- [NZB Hydra](#nzb-hydra)
	- [Jackett](#jackett)
6. [Torrent Cleanup Script](#6-torrent-cleanup-script)
7. [Plex Autoscan](#7-plex-autoscan)
8. [Adding the Movies Path](#8-adding-the-movies-path)

<!-- /TOC -->

---


## 1. Accessing Radarr
1. To access Radarr, visit https://radarr._yourdomain.com_


## 2. General Settings

1. Click "Settings" -> "General".
1. Click "Show Advanced Settings".
1. Set your branch to `nightly`, like below.

    ![Radarr Branch](http://i.imgur.com/QA8aqip.png)

1. Set "Authentication" to `Forms`, then set a username and password.
1. Click "Save".



## 3. Media Management

1. Click "Settings" -> "Media Management".

1. Enable "Rename movies".

1. Set your preferred naming format.

1. Disable "Analyse video files".

1. Disable "Use hardlinks instead of copy".

1. Click "Save".



## 4. Download Clients

1. Click "Settings" -> "Download Client".

1. Enable "Completed Download Handling" and "Remove" under it.

### NZBGet

1. Add a new "NZBGet" download client.
1. Use `nzbget` as "Host", `6789` for "Port", and `radarr` (case sensitive) for "Category". Replacing the "Username" and "Password" with your own.
1. Your settings will look like this:

    ![Radarr NZBGet Downloader](http://i.imgur.com/Q8ULGOu.png)

1. Click "Save" to add NZBGet.


### ruTorrent

1. Add a new "rTorrent" download client.
1. Use `rutorrent` as "Host", `80` for "Port", and `radarr` for "Category". Replacing the "Username" and "Password" with the one you set in [[Configuring Settings]].
1. Your settings will now look like this:

    ![Radarr ruTorrent Downloader](http://i.imgur.com/XHB6NN2.png)

1. Click "Save" to add ruTorrent.



## 5. Indexers

### NZB Hydra

1. Click "Settings" -> "Indexers".

1. Click Add Indexer (`+`).

1. Select "Newznab".  

1. Add the following:

   1. Name: NZB Hydra

   1. Enable RSS Sync: _your preference_

   1. Enable Search: _your preference_

   1. URL: `nzbhydra:8080`

   1. API Key: NZB Hydra API Key (see [[NZB Hydra]]).

1. Your settings will look like this:

    ![Radarr NZB Hydra](http://i.imgur.com/6wMQNRV.png)

1. Click "Save" to add NZB Hydra.

### Jackett

Note: Each Indexer will need to be added separately.

1. Click "Settings" -> "Indexers".

1. Click Add Indexer (`+`)

1. Select "Torznab".  

1. Add the following:

   1. Name: Indexer Name

   1. Enable RSS Sync: _your preference_

   1. Enable Search: _your preference_

   1. Host: Indexer's Torznab Feed (see [[Jackett|Jackett#3-adding-indexers-to-sonarrradarr]])

   1. API Key: Jackett API Key (see [[Jackett|Jackett#3-adding-indexers-to-sonarrradarr]])


1. Your settings will look like this:

    ![Radarr Jackett](http://i.imgur.com/QWPYWaY.png)

1. Click "Save" to add the indexer.




## 6. Torrent Cleanup Script

This custom script, will cleanup torrents from ruTorrent that were auto-extracted, but still being seeded. So if it detects that .rar files are in the folder that Radarr just imported from, it will delete the imported video file(s), leaving just the .rar files for seeding.

1. Click "Settings" -> "Connect".

1. Add a new "Custom Script".

1. Add the following:

   1. Name: Torrent Cleanup

   1. On Grab: `No`

   1. On Download: `Yes`

   1. On Upgrade:  `Yes`

   1. On Rename:`No`

   1. Path: `/scripts/torrent/TorrentCleanup.py`

   1. Arguments:`radarr`


1. The settings will look like this:

    ![Radarr Torrent Cleanup Script CloudBox](http://i.imgur.com/PUNAGed.png)


1. Click "Save" to add the Torrent Cleanup script.


## 7. Plex Autoscan

1. Click "Settings" -> "Connect".

1. Add a new "Webhook".

1. Add the following:

   1. Name: Plex Autoscan

   1. On Grab: `No`

   1. On Download: `Yes`

   1. On Upgrade:  `Yes`

   1. On Rename:`No`

   1. URL: [[Plex Autoscan URL|Plex-Autoscan#1-obtaining-the-plex-autoscan-url]]

   1. Method:`POST`


1. The settings will look like this:

    ![Radarr Plex Autoscan](http://i.imgur.com/Pg3t6xz.png)


1. Click "Save" to add Plex Autoscan.

## 8. Adding the Movies Path
1. When you are ready to add your first movie to Radarr, click the "Path" drop-down and select "Add a different path".

1. Click the blue "Browse" button, select `movies`, scroll to the bottom and select "OK".

1. Click the green "check" button to add the path.

1. All movies added now will have that path set.
