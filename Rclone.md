## Setting up Rclone

1. Run the command: `rclone config`. 

1. Select `n` to add a new remote. 

1. Type the Rclone remote you specified in [[settings.yml|Configuring Settings]] (default is `google` in lowercase) and press `enter`.

1. Type the number corresponding for "Google Drive" and press `enter`. 

1. Get a [[Google Drive API Client ID and Client Secret]].

1. Paste in the "Client ID" and press `enter`.

1. Paste in the "Client Secret" and press `enter`.

1. Type `n` for "remote or headless machine" and press `enter`.

1. Copy the link the screen shows and paste it in your browser on the host computer. Login with your Google account, if asked, and click `Allow`. You will copy the `verification code` from your browser, paste it at the prompt, and press `enter`.     

   _Note: You must use the same Google account as the one you are planning to use for Google Drive (see [[Prerequisites|Prerequisites#3-google-drive-account]])._

1. Type `y` to confirm it is ok and press `enter`. 

1. Type `q` to quit.


## Rclone already setup with Google Drive
If you have Rclone already setup, you will have an existing rclone configuration file (i.e `rclone.conf`). Edit this file and rename the Google Drive remote to what you have specified in [[settings.yml|Configuring Settings]] (default is `google` in lowercase). Copy this file into `/opt/rclone/`.

