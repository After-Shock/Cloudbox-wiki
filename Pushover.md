With [Pushover](https://pushover.net/), you can have Cloudbox send you messages during certain tasks (e.g. every time UnionFS Cleaner runs). With more tasks planned to be added later. To have that setup, follow the steps below. 

## The Basics

1. Create a [Pushover](https://pushover.net/login) account.

1. Get a Pushover license (they are cheap and worth it).  They have 3 separate ones for different device types (i.e. Android, iOS, or desktop PC). You'll need to get the license for the device where you want the messages to go. 

1. Pushover supported app

   - [Android](https://pushover.net/clients/android)

   - [iOS](https://pushover.net/clients/ios)

   - Desktop PC: [Pullover](https://github.com/cgrossde/Pullover) (free, open source, multi platform client, and my personal favorite) or you can enable them via Chrome, Firefox, Safari desktop notifications. 

1. Get your User Key (click the Pushover logo at the top left to take you there once your signed in). 

1. An "Application API Token" (one per app)

   - Pushover -> "Your Applications" -> ["Create an Application/API Token"](https://pushover.net/apps/build)

   - Fill in: 
     - Name (name of the Cloudbox app)

     - Type (Application or Script)

     - Description (optional)

     - URL (optional)

     - Icon (optional)

   - Click "Create Application".

## UnionFS Cleaner

