
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:1 -->

1. [Accessing Ombi](#1-accessing-ombi)
2. [Initial Setup](#2-initial-setup)
3. [Settings](#3-settings)

<!-- /TOC -->
---
## 1. Accessing Ombi

 - To access Ombi, visit https://ombi._yourdomain_.com


## 2. Initial Setup

1. First time you go to the Ombi page, you will be presented with the "Welcome to Ombi" screen. Click the orange-colored `Next` link to be taken to the "Media Server Selection" page.
  
  ![](https://i.imgur.com/w69ajDs.png)

2. Select your media server of choice `emby` or `PLEX` by clicking the respected logo or `Skip` this portion for now.

  ![](https://i.imgur.com/WCDwAde.png)

3. Plex Authentication: enter your username and password for your Plex server and hit the `Request Token` button.
 
  ![](https://i.imgur.com/KosZzF2.png)

4. Emby Authentication (if installed optionally): enter your Emby hostname or IP address along with the Api Key for your Emby media server.  Tic the SSL box if you are using https://emby._mydomain_.com

  ![](https://i.imgur.com/fWr5UhM.png)

5. Whether you selected `Plex` or `emby` once you enter the proper authentication info and all goes well you will see the "Sign in" prompt asking you for a Username and Password, simply enter your credentials from the previous screen in order to sign in.

    ![](https://i.imgur.com/e7dkVAd.png)
    
        
## 3. Settings

1. Once logged in, find the `Settings` menu button in the upper right corner and click it. now be taken to the "General" settings page. You may select whatever options you like here. Click `Update Settings` to save changes.

    ![](https://i.imgur.com/zw5K5z3.png)

1. On the "Authentication" settings page

    - It is advised to have both `Enable user authentication` and `Require users to login with their passwords` enabled (at the very least `Enable user authentication` enabled).

    - To have your Plex Authorization token automatically retrieved, fill in your `Plex Username` and `Plex Password` and click the `Get Token` button. When this is successful, you will get the "Successfully got token!" message and the `Plex authorization token` textbox will be filled in.

    - Click `Update Settings` to save changes.

    ![](https://i.imgur.com/vd35F5e.png)

    ![](https://i.imgur.com/gLucVsz.png)


1. On the "Radarr" settings page:

   _Note: There are some slight differences in the settings for Feeder / Plex setups. See notes below._ 


    - Check "Enable Radarr"

    - "Radarr server IP or Hostname": `radarr`

       - _For a Feeder / Plex setup, use `radarr.yourdomain.com` (or the IP address of your Feeder box) instead._


    - "Radarr server port":`7878`

       - _For a Feeder / Plex setup, use `443` instead._


    - "Radarr API key": [[Your Radarr API Key|First-Time-Install: Radarr#9-retrieving-the-api-key]]


    - "Enable Radarr SSL": `disabled`.

       - _For Feeder / Plex setup, set it to `enabled`._


    - Click `Update Settings`.

    - Click `Test Radarr server`. The button will update to show "Success!".

    - Click `Get Profiles` and choose your preferred "Download quality profile for Radarr".

    - "Root save directory for movies": `/movies`.

    - Click `Update Settings`.

    ![](https://i.imgur.com/YKEPArN.png)

1. On the "Sonarr" settings page:

   _Note: There are some slight differences in the settings for Feeder / Plex setups. See notes below._ 

    - Check "Enable Sonarr"

    - "Sonarr server IP or Hostname": `sonarr`

       - _For Feeder / Plex setup, use `sonarr.yourdomain.com` (or the IP address of your Feeder box) instead._

    - "Sonarr server port":`8989`

       - _For Feeder / Plex setup, use `443` instead._

    - "Sonarr API key": [[Your Sonarr API Key|First-Time-Install: Sonarr#9-retrieving-the-api-key]]

    - "Enable Sonarr SSL": `disabled`.

       - _For Feeder / Plex setup, set it to `enabled`._


    - Click `Update Settings`.

    - Click `Test Sonarr server`. The button will update to show "Success!".

    - Click `Get Profiles` and choose your preferred "Download quality profile".

    - "Root save directory for TV shows": `/tv`.

    - Click `Update Settings`.

    _Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed.

    ![](https://i.imgur.com/fqnAyI5.png)

1. Click `Sign Out` to exit Settings.
