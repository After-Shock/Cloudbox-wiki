
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:1 -->

1. [Accessing Ombi](#1-accessing-ombi)
2. [Initial Setup](#2-initial-setup)
3. [Settings](#3-settings)
4. [Plex Settings](#4-plex-settings)
5. [Radarr Settings](#5-radarr-settings)
6. [Sonarr Settings](#6-sonarr-settings)

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

1. On the "Configuration" settings page, find the Authentication section.

    - It is advised to have both `Enable Plex OAuth` and leave `Allow users to login without a password` disabled.
    ![](https://i.imgur.com/XHXc1Wx.png)
    

## 4. Plex Settings
Find the Media Server menu and select `Plex`.  Enter your Plex username and password, then his the `Load Servers` button.  This will scan for all of the Plex servers associated with the credentials you entered. Use the `Servers` button to hightlight the server you wish to configure Ombi with. While doing this will fill in the local hostname or IP section, it's best practice to use the dynamic name of `plex` in the Hostname field as seen in the image:

    ![](https://i.imgur.com/RUZW88d.png)
    
1.  Hit the `Submit` button and then `Test Connectivity` button to verify Ombi is able to connect to your Plex instance.


## 5. Radarr Settings

1. Under Movies menu section you will find the "Radarr" settings page:

   _Note: There are some slight differences in the settings for Feeder / Plex setups. See notes below._ 


    - Check "Enable Radarr"

    - "Radarr server IP or Hostname": `radarr`

       - _For a Feeder / Plex setup, use `radarr.yourdomain.com` (or the IP address of your Feeder box) instead._


    - "Radarr server port":`7878`

       - _For a Feeder / Plex setup, use `443` instead._


    - "Radarr API key": [[Your Radarr API Key|First-Time-Install: Radarr#9-retrieving-the-api-key]]


    - "Enable Radarr SSL": `disabled`.

       - _For Feeder / Plex setup, set it to `enabled`._


    - Click `Submit`.

    - Click `Test Connectivity`. A fly in notification in the upper right corner will show "Successfully connected to Radarr!".

    - Click `Get Quality Profiles` and choose your preferred "Download quality profile for Radarr".

    - Click `Get Root Folders` and choose your preferred Root Folder, most cases it's simply `/movies`. 
    
    - Select the desired "Default Minimun Availability"

    - Click `Submit`.

     ![](https://i.imgur.com/J7MTPaz.png)
    
## 6. Sonarr Settings

1. Under TV menu section you will find the "Sonarr" settings page:

   _Note: There are some slight differences in the settings for Feeder / Plex setups. See notes below._ 

    - Check "Enable Sonarr"

    - "Sonarr server IP or Hostname": `sonarr`

       - _For Feeder / Plex setup, use `sonarr.yourdomain.com` (or the IP address of your Feeder box) instead._

    - "Sonarr server port":`8989`

       - _For Feeder / Plex setup, use `443` instead._

    - "Sonarr API key": [[Your Sonarr API Key|First-Time-Install: Sonarr#9-retrieving-the-api-key]]

    - "Enable Sonarr SSL": `disabled`.

       - _For Feeder / Plex setup, set it to `enabled`._


    - Click `Submit`.

    - Click `Test Connectivity`. A fly in notification in the upper right corner will show "Successfully connected to Sonarr!".

    - Click `Get Quality Profiles` and choose your preferred "Download quality profile".

    - Click `Get Root Folders` and choose your preferred Root Folder, most cases it's `/tv` for TV shows. 
    
    - Enable season folders if you wish. 
   
    - Click `Submitt`.

    _Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed.

    ![](https://i.imgur.com/HXYBT5K.png)


