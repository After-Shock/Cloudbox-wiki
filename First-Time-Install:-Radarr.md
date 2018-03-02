<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:0 -->

1. [Accessing Radarr](#1-accessing-radarr)
2. [General Settings](#2-general-settings)
3. [Media Management](#3-media-management)
4. [Download Clients](#4-download-clients)
	- [NZBGet](#nzbget)
	- [ruTorrent](#rutorrent)
5. [Indexers](#5-indexers)
	- [NZBHydra](#nzbhydra)
	- [Jackett](#jackett)
6. [Torrent Cleanup Script](#6-torrent-cleanup-script)
7. [Plex Autoscan](#7-plex-autoscan)
8. [Adding the Movies Path](#8-adding-the-movies-path)
9. [Retrieving the API Key](#9-retrieving-the-api-key)

<!-- /TOC -->

---


## 1. Accessing Radarr

- To access Radarr, visit https://radarr._yourdomain.com_


## 2. General Settings

1. Click "Settings" -> "General".
1. Click "Show Advanced Settings".
1. Set "Authentication" to `Forms`, then set a username and password.

1. Under "Updates":
   
   1. set "Branch" to `nightly` (type it in)

      ![Radarr Branch](http://i.imgur.com/QA8aqip.png)

   1. set "Automatic" to "off".  

1. Click "Save".



## 3. Media Management

1. Click "Settings" -> "Media Management".

1. Enable "Rename movies".

1. Enable "Replace Illegal Characters".

1. Set your preferred naming format.

1. Disable "Analyse video files".

1. Click "Save".

_Tip: [[My file naming preferences|https://github.com/desimaniac/docs/blob/master/my_sonarr_and_radarr_naming_preferences.md]], for whoever is interested._


## 4. Download Clients

1. Click "Settings" -> "Download Client".

1. Enable "Completed Download Handling" and "Remove" under it.

### NZBGet

1. Add a new "NZBGet" download client.

1. Add the following:

   1. Name: NZBGet

   1. Enable: `Yes`

   1. Host: `nzbget`

   1. Port: `6789`

   1. Username:  [[Your NZBGet Username|First-Time-Install: NZBGet]]

   1. Password:  [[Your NZBGet Password| First-Time-Install: NZBGet]]

   1. Category: `radarr`

   1. Use SSL: `No`

   1. Add Paused: `No`

1. Your settings will look like this:

    ![Radarr NZBGet Downloader](https://i.imgur.com/JbN4EcK.png)

1. Click "Save" to add NZBGet.


### ruTorrent

1. Add a new "rTorrent" download client.

1. Add the following:

   1. Name: ruTorrent

   1. Enable: `Yes`

   1. Host: `rutorrent`

   1. Port: `80`

   1. URL Path: `RPC2`

   1. Use SSL: `No`

   1. Username: [[Your ruTorrent Username|First Time Install: Configuring Settings]]

   1. Password: [[Your ruTorrent Password|First Time Install: Configuring Settings]]

   1. Category: `radarr`

   1. Directory: _Leave Blank_

1. Your settings will now look like this:

    ![Radarr ruTorrent Downloader](http://i.imgur.com/XHB6NN2.png)

1. Click "Save" to add ruTorrent.



## 5. Indexers

After adding in your favorite [[indexers| Basics: Prerequisites#6-preferred-downloading-method]], you may add the following ...

### NZBHydra

1. Click "Settings" -> "Indexers".

1. Click Add Indexer (`+`).

1. Select "Newznab".  

1. Add the following:

   1. Name: NZB Hydra

   1. Enable RSS Sync: _Your Preference_

   1. Enable Search: _Your Preference_

   1. URL: `http://nzbhydra:5075`

   1. API Key: [[Your NZB Hydra API Key|First-Time-Install: NZBHydra#api-key]]

   1. Additional Parameters: _Leave Blank_

1. Your settings will look like this:

    ![Radarr NZB Hydra](https://i.imgur.com/ZWYqzCS.png)

1. Click "Save" to add NZB Hydra.

Note: The "Test" will keep failing until you add an indexer in [[NZBHydra|First-Time-Install: NZBHydra]].

### Jackett

Note: Each Indexer will need to be added separately.

1. Click "Settings" -> "Indexers".

1. Click Add Indexer (`+`)

1. Select "Torznab".  

1. Add the following:

   1. Name: Indexer Name

   1. Enable RSS Sync: _Your Preference_

   1. Enable Search: _Your Preference_

   1. URL: [[Indexer's Torznab Feed|First-Time-Install: Jackett#3-adding-indexers-to-sonarrradarr]]

   1. API Key: [[Your Jackett API Key|First-Time-Install: Jackett#3-adding-indexers-to-sonarrradarr]]

   1. Additional Parameters: _Leave Blank_

1. Your settings will look like this:

    ![Radarr Jackett](https://i.imgur.com/T9vrrAW.png)

1. Click "Save" to add the indexer.




## 6. Torrent Cleanup Script

This custom script, will cleanup torrents from ruTorrent that were auto-extracted, but still being seeded. So if the script detects that .rar/.zip files are in the folder that Sonarr just imported from, it will delete the imported video file(s), leaving just the .rar/.zip files for seeding.

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

   1. URL: [[Your Plex Autoscan URL|First-Time-Install: Plex-Autoscan#3-obtaining-the-plex-autoscan-url]]

   1. Method:`POST`

   1. Username: _Leave Blank_

   1. Password: _Leave Blank_

1. The settings will look like this:

    ![Radarr Plex Autoscan](https://i.imgur.com/niiQNPe.png)


1. Click "Save" to add Plex Autoscan.



## 8. Adding the Movies Path
1. When you are ready to add your first movie to Radarr, click the "Path" drop-down and select "Add a different path".

1. Click the blue "Browse" button, select the `movies` folder, scroll to the bottom, and select "OK".

1. Click the green "check" button to add the path.

1. All movies added now will have that path set.

## 9. Retrieving the API Key

This is used during the setup of [[Plex Requests | First-Time-Install: Plex Requests]] and [[Organizr | First-Time-Install: Organizr]]. 

* Go to "Settings" -> "General" -> "Security" -> "API Key".
