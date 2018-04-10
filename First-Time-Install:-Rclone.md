Rclone is used by [[UnionFS Cleaner]] and [[Backup|Backup-and-Restore]] to upload your media and backup, respectively. 


## New Rclone Setup

1. Run the command: 

   ```
   rclone config
   ``` 

1. `Rclone Config Menu:`

   ```
   n
   ```
   (add a new remote).

1. `Remote Name:`

   ```
   google
   ```

    _Note: This is the same is specified under Rclone Renote under [[settings.yml|First Time Install: Configuring Settings]] (default is `google` in lowercase)._

1. `Type of storage to configure:`

   ```
   drive
   ```

   _Note: You could also type in the number for Google Drive._ 

1. Create a [[Google Drive API Client ID and Client Secret]] for Rclone.

1. `Client ID`:

   `Client ID` from Step 5.

1. `Client Secret`:

   `Client Secret` from Step 5.

1. (New for Rclone 1.40) `Scope that rclone should use when requesting access from drive:`

   ```
   drive
   ```
   (Full access all files, excluding Application Data Folder)

   _Note: You can also type in the number for the option._ 

1. (New for Rclone 1.40) `ID of the root folder`: 

   Leave blank and press `enter`.

1. (New for Rclone 1.40) `Service Account Credentials JSON file path:`

   Leave blank and press `enter`.

1. `Use auto config?`

   ```
   n
   ```
   
   (you are working on a remote or headless machine)

1. `If your browser doesn't open automatically go to the following link:`

   - Copy the link the screen shows and paste it in your browser on the host computer. 

   - If asked, login with your Google account and click `Allow`. 

      - _Note: You must use the same Google account as the Google Drive one you intend to use (see [[Prerequisites| Basics: Prerequisites#4-google-drive-account]])._

   - Copy the `verification code`.     


1. `Enter verification code>`

   `verification code` from above. 

1. `Configure this as a team drive?`

   ```
   n
   ```
   (no)

1. `Yes this is OK`

   ```
   y
   ```
   (yes)

1. `Rclone Config Menu:`

   ```
   q
   ```
   (Quit config)



## Rclone already setup with Google Drive

1. Edit your rclone configuration file (i.e `rclone.conf`). 

1. Rename the Google Drive remote to what you have specified in [[settings.yml|First Time Install: Configuring Settings]] (default is `google` in lowercase). 

1. Copy this file into `~/.config/rclone/`.

