## Setting up Rclone

1. Run the command: `rclone config`. 
1. Select `n` to add a new remote. 
1. Type `google` as the name (_lowercase_) and press `enter`.
1. Type the number corresponding to "Google Drive" and press `enter`. 
1. Get a Google API "client ID" and "client secret" (see [[How to get a Google Drive API client ID and client secret]]).
1. Paste in the "client id" and press `enter`.
1. Paste in the "client secret" and press `enter`.
1. Type `n` for remote/headless machine and press `enter`.
1. Copy the link the screen shows and paste it in your browser on the host computer. Login with your Google account and click `Allow`, if asked. You will copy the `verification code` from your browser, paste it at the prompt, and press `enter`.
1. Type `y` to confirm it is ok and press `enter`. 
1. Type `q` to quit.


## Rclone already setup with Google Drive
If you have Rclone already setup, you will have an existing rclone configuration file (i.e `rclone.conf`). Edit this file and rename the Google Drive remote to `google` and copy this file into `/opt/rclone`.

