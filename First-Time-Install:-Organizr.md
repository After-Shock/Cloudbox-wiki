<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:1 -->

1. [Intro](#1-intro)
2. [Accessing Organizr](#2-accessing-organizr)
3. [Initial Setup](#3-initial-setup)
4. [Settings](#4-settings)
	- [Tabs](#tabs)
	- [Homepage](#homepage)

<!-- /TOC -->
---
## 1. Intro

[Organizr](https://organizr.app/) (by CauseFX) is a web-based, HTPC server organizer, that allows you to manage various tools and programs within tabs. Also supports user management, allowing for non admin users or guests to access certain web-pages via Organizr, even if it is behind HTTP authentication. 

![](https://i.imgur.com/ztDFbxZ.jpg)

## 2. Accessing Organizr

- To access Organizr, visit https://organizr._yourdomain_.com

## 3. Initial Setup

1. First time you go to the Organizr page, you will be presented with a "DATABASE PATH" screen. Leave "Database Location" as `/config/www` and set the "Timezone" to where you reside. Click "SAVE LOCATION".

    ![Database Path](https://i.imgur.com/6LaFMFW.png)

1. Next screen will ask you to create an admin account for Organizr. Fill in your information and click "REGISTER".

    ![Create Admin](https://i.imgur.com/O20Swhy.png)


## 4. Settings

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


  - Note: If Sonarr or Radarr are lagging a lot, you may set it to a specific page in each. (e.g. Sonarr: https://sonarr.yourdomain.com/calendar ; Radarr: https://radarr.yourdomain.com/activity/history)


### Homepage

1. Click "Edit Homepage" on the left menu, to be taken to the "Edit Homepage" page.

    ![Edit Homepage](https://i.imgur.com/Ed0Ir4X.png)

1. Click the Plex icon at the top.

    - Set "Plex URL": `http://plex:32400`

      - _Note: For Feeder / Plex setups, you will use `https://plex.yourdomain.com:32400`._

    - Click "GET PLEX TOKEN", fill in your Plex login in the popup window, and click "Get PLEX Token".

    - Set your preferred options below.

    - Click "SAVE".

    ![  ](https://i.imgur.com/v6EdCLt.png)

1. Click the Sonarr icon at the top.

    - Set "Sonarr URL": `http://sonarr:8989`

    - Set "Sonarr API Key": [[Your Sonarr API Key|First-Time-Install: Sonarr#9-retrieving-the-api-key]]

    - Click "SAVE".

    ![  ](https://i.imgur.com/YHAJFyT.png)

1. Click the Radarr icon at the top.

    - Set "Radarr URL": `http://radarr:7878`

    - Set "Radarr API Key": [[Your Radarr API Key|First-Time-Install: Radarr#9-retrieving-the-api-key]]

    - Click "SAVE".

    ![  ](https://i.imgur.com/IL1moq1.png)

1. Click the NZBGet icon at the top.

    - Set "NZBGet URL": `http://nzbget:6789`

    - For "Username" / "Password": fill in your NZBGet login (see [[NZBGet|First-Time-Install: NZBGet#2-setup]])

    - Click "SAVE".

    ![  ](https://i.imgur.com/zFTJ1Or.png)
