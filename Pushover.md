## What is Pushover?

[Pushover](https://pushover.net/faq) is service to receive instant push notifications on your phone or tablet from a variety of sources. With Cloudbox, you can have notifications during many different tasks or events (e.g. every time UnionFS Cleaner runs).

-  Some examples:

   - Cloudbox Backup (coming soon)

     ![](https://i.imgur.com/fDWzmxM.png)

   - UnionFS Cleaner Pushover alerts:
  
     ![](https://i.imgur.com/HUUZ91a.png)
  




## The Basics

Listed below are the things you'll need from Pushover's site. 

1. [Pushover](https://pushover.net/login) account.

1. Pushover license(s) 

   - They have 3 separate ones for different device types (i.e. Android, iOS, or desktop PC). You'll need to get the license for the device where you want the messages to go. 

1. [Pushover Device Client](https://pushover.net/clients)
   - [Android](https://pushover.net/clients/android)
   - [iOS](https://pushover.net/clients/ios)
   - Desktop PC: [Pullover](https://github.com/cgrossde/Pullover) (free, open source, multi platform client, and my personal favorite). You can also get the via browser desktop notifications (i.e. Chrome, Firefox, Safari).

1. Your User Key (click the Pushover logo at the top left to take you there once your signed in). 

1. Application API Token (one per app)

   - Pushover -> Your Applications -> [Create an Application/API Token](https://pushover.net/apps/build)

   - Fill in: 
     - Name (app/task name)
     - Type (Application or Script)
     - Description (optional)
     - URL (optional)
     - Icon (optional)
   - Click "Create Application".


## Cloudbox Backup (coming soon)

To have Pushover send you alerts every time Cloudbox backup task starts and finishes, follow to steps below. 

1. Edit the settings.yml file. 

   ```bash
     nano ~/cloudbox/settings.yml
   ```

1. Type in your Pushover User Key and the Application Token, without quotes, in the "backup" section.

   ```yaml
     backup:
   
       pushover_app_token:
       pushover_user_key:
   ```

1. `Ctrl-x`, `y`, then `enter`.

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

1. `Ctrl-X` and `Y` to save.

1. UnionFS Cleaner will restart itself when it detects config.json has changed.


## PlexPy

Pushover can send you notifications whenever an event occurs with Plex (e.g. someone starts watching something,  new media is added)

1. Enable notifications: [PlexPy](PlexPy#1-accessing-plexpy) -> Settings -> Notification Agents -> Click the gray "bell" icon next to "Pushover" -> and select when you want to be alerted -> Click "close". The "bell" icon will turn yellow. 

1. Add in your Pushover info: Click the "gear" icon next to "Pushover" -> Type in your Pushover User Key and the Application Token (you can click the "Test Notification" to check if it's working ok) -> Click "Save". 


## Plex Requests

Pushover can send notifications whenever an event occurs in Plex Requests (e.g. media is requested).

- [Plex Requests](Plex-Requests#1-accessing-plex-requests) -> Admin -> Notifications -> check "Enable Pushover notifications" and type in your Pushover User Key and the Application Token (you can click the "Test Pushover" to check if it's working ok) -> Click "Update Settings".
