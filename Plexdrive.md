1. Get a new Google API "Client ID" and "Client Secret" (see [[this | How to get a Google Drive API Client ID and Client Secret]]).

    Note: this will be different from the Rclone one. You can use the same Google account; but just create a different project for Plexdrive. 

1. Run this command:

    ```bash
    /opt/plexdrive/plexdrive mount -v 3 --refresh-interval=1m --chunk-check-threads=8 --chunk-load-threads=8 --chunk-load-ahead=4 --max-chunks=250 --fuse-options=allow_other,read_only --config=/opt/plexdrive --cache-file=/opt/plexdrive/cache.bolt /mnt/plexdrive
    ```
1. When prompted for the "client id", paste in the Google API Client ID and press `enter`.

1. When prompted for the "client secret", paste in the Google API Client Secret and press `enter`.

1. Copy the link on the screen  and paste it in your host computer's internet browser. Login with your Google account, if asked, and click `Allow`. You will copy the `authorization code` from your browser, paste it at the prompt, and press `enter`.


   Note 1: You must use the same Google account as the one you are planning to use for Google Drive (see [[Prerequisites|Prerequisites#4-google-drive-account]]).

   Note 2: If you keep getting the prompt for the authorization code, you might have used an incorrect Client ID/Secret. Remove the `config.json` and `token.json` files from `/opt/plexdrive/` and retry setup.

1. When you see `First cache build process started...`, press `ctrl`+`c` on your keyboard to exit.

   ![](http://i.imgur.com/bDTmXbT.png)

    Note: Any errors, such as, `WARNING: Could not get object root from API` or `mount helper error`, means this failed somewhere and you need to figure out why. 

1. Run the following commands (one by one):

    ```bash
    sudo systemctl enable plexdrive
    sudo systemctl start plexdrive
    ```
1. Verify Plexdrive is running ok:

    ```bash
    sudo systemctl status plexdrive
    ```

    You should see it as being `active (running)` ...

    ```bash
   plexdrive.service - Plexdrive
   Loaded: loaded (/etc/systemd/system/plexdrive.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2017-10-14 12:41:01 CEST; 8h ago
   Main PID: 1025 (plexdrive)
   Tasks: 21
   Memory: 2.7G
   CPU: 23.494s
   CGroup: /system.slice/plexdrive.service
           └─1025 /opt/plexdrive/plexdrive mount -v 3 --refresh-interval=1m --chunk-check-threads=8 --chunk-load-threads=8 --chunk-
    ```

    If you see an error here, check [[FAQ]] for possible fix(es). 

1. You should now be able to see all your media files in `/mnt/unionfs/Media` (i.e. on Google drive and your server, combined).

   If you are not able to, then something was done incorrectly during the setup of Plexdrive (i.e. this page) and/or your media is not located in the correct folder in Google Drive (see [[Prerequisites|Prerequisites#4-google-drive-account]] and [[Paths|Paths#google-drive-paths]]).