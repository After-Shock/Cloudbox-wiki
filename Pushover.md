## What is Pushover?

With [Pushover](https://pushover.net/), you can have Cloudbox send you messages during certain tasks (e.g. every time UnionFS Cleaner runs). With more tasks planned to be added later. 

-  Some examples:

   - UnionFS Cleaner Pushover alerts:
  
     ![](https://i.imgur.com/HUUZ91a.png)
  
   - Cloudbox Backup (coming soon)

     ![](https://i.imgur.com/fDWzmxM.png)



## The Basics

Listed below are the things you'll need from Pushover's site. 

1. [Pushover](https://pushover.net/login) account.

1. Pushover license(s) 

   - They have 3 separate ones for different device types (i.e. Android, iOS, or desktop PC). You'll need to get the license for the device where you want the messages to go. 

1. [Pushover Device Client](https://pushover.net/clients)
   - [Android](https://pushover.net/clients/android)
   - [iOS](https://pushover.net/clients/ios)
   - Desktop PC: [Pullover](https://github.com/cgrossde/Pullover) (free, open source, multi platform client, and my personal favorite) or you can enable them via Chrome, Firefox, Safari desktop notifications. 
1. Your User Key (click the Pushover logo at the top left to take you there once your signed in). 

1. Application API Token (one per app)

   - Pushover -> "Your Applications" -> ["Create an Application/API Token"](https://pushover.net/apps/build)

   - Fill in: 
     - Name (cname of the Cloudbox app)
     - Type (Application or Script)
     - Description (optional)
     - URL (optional)
     - Icon (optional)
   - Click "Create Application".



## UnionFS Cleaner

To have UnionFS Cleaner send you alerts every time it starts and finishes, follow to steps below. 

1. Edit the Unionfs Cleaner config.json file:

    ```
    nano /opt/unionfs_cleaner/config.json
    ```

1. Fill in your Pushover User Key and the Application API/Token within the quotes ("").

   ```json
    "pushover_app_token": "",
    "pushover_user_token": "",
   ```

1. `Ctrl-X` and `Y` to save.

1. UnionFS Cleaner will restart itself when it detects config.json has changed.

## Cloudbox Backup

To have UnionFS Cleaner send you alerts every time it starts and finishes, follow to steps below. 
