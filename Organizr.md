<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:1 -->

1. [Accessing Organizr](#1-accessing-organizr)
2. [Initial Setup](#2-initial-setup)
3. [Settings](#3-settings)
	- [Tabs](#tabs)
	- [Homepage](#homepage)

<!-- /TOC -->
---

The following guide will help you setup Organizer. If you would like an alternative solution, take a look at [[Nativefier]].

## 1. Accessing Organizr

- To access Organizr, visit http://organizr._yourdomain_.com

## 2. Initial Setup

1. First time you go to the Organizr page, you will be presented with a "DATABASE PATH" screen. Leave "Database Location" as `/config/www` and set the "Timezone" to where you reside. Click "SAVE LOCATION".

    ![Database Path](https://i.imgur.com/6LaFMFW.png)

1. Next screen will ask you to create an admin account for Organizr. Fill in your information and click "REGISTER".

    ![Create Admin](https://i.imgur.com/O20Swhy.png)


## 3. Settings

1. You will now be taken to the main Organizr Page.

    ![Organizr](https://i.imgur.com/94QoAcd.png)

### Tabs

1. Click "Edit Tabs" on the left menu, to be taken to the "Edit Tabs" page.

    ![Edit Tabs 1](https://i.imgur.com/f8ozDau.png)

    ![Edit Tabs 2](https://i.imgur.com/ZR5p6WF.png)

1. Click "+ New Tab". You will be prompted for information regarding the tab.

    ![](https://i.imgur.com/mSPEngl.png)

1. You will need to create multiple tabs with the information below. Once you are done adding them, click "SAVE TABS".

    | Tab Name      | Tab URL                             | Icon URL                      | Active | User | Guest | No iFrame | Default |
    | ------------- | ----------------------------------- | ----------------------------- |:------:|:----:|:-----:|:---------:|:-------:|
    | Organizr      | homepage.php                        | images/organizr_logo.png      |   Y    |  Y   |   N   |     N     |    Y    |
    | Portainer     | https://portainer.yourdomain.com    | images/organizr.png (default) |   Y    |  Y   |   N   |     N     |    N    |
    | Sonarr        | https://sonarr.yourdomain.com       | images/sonarr.png             |   Y    |  Y   |   N   |     N     |    N    |
    | Radarr        | https://radarr.yourdomain.com       | images/radarr.png             |   Y    |  Y   |   N   |     N     |    N    |
    | NZBGet        | https://nzbget.yourdomain.com       | images/nzbget.png             |   Y    |  Y   |   N   |     N     |    N    |
    | Rutorrent     | https://rutorrent.yourdomain.com    | images/rutorrent.png          |   Y    |  Y   |   N   |     N     |    N    |
    | NZBHydra      | https://nzbhydra.yourdomain.com     | images/hydra.png              |   Y    |  Y   |   N   |     N     |    N    |
    | Jackett       | https://jackett.yourdomain.com      | images/jackett.png            |   Y    |  Y   |   N   |     N     |    N    |
    | Plex          | https://plex.yourdomain.com         | images/plex.png               |   Y    |  Y   |   N   |     N     |    N    |
    | PlexPy        | https://plexpy.yourdomain.com       | images/plexpy.png             |   Y    |  Y   |   N   |     N     |    N    |
    | Plex Requests | https://plexrequests.yourdomain.com | images/plexrequests.png       |   Y    |  Y   |   N   |     N     |    N    |


    ![Tab Settings](https://i.imgur.com/UgVZrAN.png)


  - Note: If Sonarr or Radarr are lagging too much, you may set it to a specific page in each. (e.g. Sonarr: https://sonarr.yourdomain.com/calendar ; Radarr: https://radarr.yourdomain.com/activity/history)


### Homepage

1. Click "Edit Homepage" on the left menu, to be taken to the "Edit Homepage" page.

    ![Edit Homepage](https://i.imgur.com/Ed0Ir4X.png)

1. Click the Plex icon at the top.

    - Set "Plex URL": `http://plex:32400`

    - Click "GET PLEX TOKEN", fill in your Plex login, and click "Get PLEX Token".

    - Set your preferred options below.

    - Click "SAVE".

    ![  ](https://i.imgur.com/v6EdCLt.png)

1. Click the Sonarr icon at the top.

    - Set "Sonarr URL": `http://sonarr:8080`

    - Set "Sonarr API Key": _Your Sonarr API Key_ (you can find this at [[Sonarr|Sonarr#1-accessing-sonarr]] --> Settings --> General)

    - Click "SAVE".

    ![  ](https://i.imgur.com/CFUtiTz.png)

1. Click the Radarr icon at the top.

    - Set "Radarr URL": `http://radarr:8080`

    - Set "Radarr API Key": _Your Radarr API Key_ (you can find this at [[Radarr|Radarr#1-accessing-radarr]] --> Settings --> General)

    - Click "SAVE".

    ![  ](https://i.imgur.com/5huf18e.png)

1. Click the NZBGet icon at the top.

    - Set "NZBGet URL": `http://nzbget:6789`

    - For "Username" / "Password": fill in your NZBGet login (see [[NZBGet|NZBGet#2-setup]])

    - Click "SAVE".

    ![  ](https://i.imgur.com/57PkVbv.png)