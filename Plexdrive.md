1. Get a new Google API "Client ID" and "Client Secret" (see [[How to get a Google Drive API Client ID and Client Secret]]).

    Note: this will be different from the Rclone one. You can use the same Google Account, but create a different project. 

1. Run this command:

    ```bash
    /opt/plexdrive/plexdrive mount -v 3 --refresh-interval=1m --chunk-check-threads=8 --chunk-load-threads=8 --chunk-load-ahead=4 --max-chunks=250 --fuse-options=allow_other,read_only --config=/opt/plexdrive --cache-file=/opt/plexdrive/cache.bolt /mnt/plexdrive
    ```
1. When prompted for the "client id", paste in the Google API Client ID and press `enter`.
1. When prompted for the "client secret", paste in the Google API Client secret and press `enter`.
1. Copy the link on the screen  and paste it in your host computer's internet browser. Login with your Google account, if asked, and click `Allow`. You will copy the `authorization code` from your browser, paste it at the prompt, and press `enter`.
1. When you see `First cache build process started...`, press `ctrl`+`c` on your keyboard to exit.

   ![](http://i.imgur.com/bDTmXbT.png)

    Note: Any errors, such as, `WARNING: Could not get object root from API` or `mount helper error`, means this failed somewhere and you need to figure out why. 

1. Run the following commands (one by one):

    ```bash
    sudo systemctl enable plexdrive
    sudo systemctl start plexdrive
    ```