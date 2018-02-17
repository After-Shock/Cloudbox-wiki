<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [What is Pushover?](#what-is-pushover)
- [Pushover Setup](#pushover-setup)
- [Cloudbox Backup](#cloudbox-backup)
- [UnionFS Cleaner](#unionfs-cleaner)
- [Plex Requests](#plex-requests)
- [PlexPy](#plexpy)
- [Sonarr and Radarr](#sonarr-and-radarr)


<!-- /TOC -->

---



## What is Pushover?

[Pushover](https://pushover.net/faq) is service that enables you to receive instant push notifications on your phone/tablet/PC from a variety of sources. With Cloudbox, you can have notifications sent with many different events.

Screenshots:

 - Mobile device (Pushover app):

   ![](https://i.imgur.com/lTdXcNU.png)



 - PC (Pullover client):
  
   ![](https://i.imgur.com/2A12nIe.png)
  





## Pushover Setup

Listed below are the things you'll need from Pushover's site. 

1. [Pushover](https://pushover.net/login) account

1. Pushover license(s) 

   - Pushover has 3 separate licenses for the different device types: Android, iOS, or PC. The cost for the license is a one-time fee of $4.99. You'll need one for the type of device you want to receive notifications on.  See their [FAQ](https://pushover.net/faq#overview-fees) for more info.

1. A [Pushover Device Client](https://pushover.net/clients)

   - [Android](https://pushover.net/clients/android)

   - [iOS](https://pushover.net/clients/ios)

   - Desktop PC: 
     
     - [Pullover](https://github.com/cgrossde/Pullover) (free, open source, multi platform client, and my personal favorite). 

     - Browser Desktop Notifications (i.e. Chrome, Firefox, Safari).

1. Your User Key 

   - Once your signed in, click the Pushover logo at the top left to take you there.

1. Application API Token (one per app)

   - Pushover -> Your Applications -> [Create an Application/API Token](https://pushover.net/apps/build)

   - Fill in: 

     - Name (app/task name)

     - Type (Application or Script)

     - Description (optional)

     - URL (optional)

     - Icon (optional)

   - Click "Create Application".


## Cloudbox Backup

To have Pushover send you alerts every time a Cloudbox backup task starts and finishes, follow to steps below. 

1. Edit the settings.yml file. 

   ```bash
     nano ~/cloudbox/settings.yml
   ```

1. Type in your Pushover User Key and the Application Token under "backup" (without quotes).

   ```yaml
     backup:
   
       pushover_app_token:
       pushover_user_key:
   ```

1. `Ctrl-x`, `y`, and `enter` to save.


Tip: If you have a Plexbox/Feederbox setup, you can create 2 different applications within Pushover specify "Plexbox Backup" and "Feederbox Backup" as their names. 

## UnionFS Cleaner

To have Pushover send you alerts every time a UnionFS Cleaner task starts and finishes, follow to steps below. 

1. Edit the Unionfs Cleaner config.json file:

    ```
    nano /opt/unionfs_cleaner/config.json
    ```

1. Type in your Pushover User Key and the Application Token within the quotes ("").

   ```json
    "pushover_app_token": "",
    "pushover_user_token": "",
   ```

1. `Ctrl-x`, `y`, and `enter` to save.

1. UnionFS Cleaner will restart itself when it detects config.json has changed.


## Plex Requests

Pushover can send notifications whenever an event occurs in Plex Requests (e.g. media is requested by someone).

- [Plex Requests](Plex-Requests#1-accessing-plex-requests) -> Admin -> Notifications -> check "Enable Pushover notifications" and type in your Pushover User Key and the Application Token (you can click the "Test Pushover" to check if it's working ok) -> Click "Update Settings".


## PlexPy

Pushover can send you notifications whenever an event occurs with Plex (e.g. someone starts watching something,  new media is added, etc)

1. Enable notifications: [PlexPy](First-Time-Install: PlexPy#1-accessing-plexpy) -> Settings -> Notification Agents -> Click the gray "bell" icon next to "Pushover" -> and select when you want to be alerted -> Click "close". The "bell" icon will turn yellow. 

1. Add in your Pushover info: Click the "gear" icon next to "Pushover" -> Type in your Pushover User Key and the Application Token (you can click the "Test Notification" to check if it's working ok) -> Click "Save". 



## Sonarr and Radarr

You can also have Sonarr and Radarr also send out alerts via Pushover when new media is added. 