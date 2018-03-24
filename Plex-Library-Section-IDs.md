# Retrieving your Plex Library Section IDs

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._

1. On the server's shell, run the following command:

    ```
    /opt/plex_autoscan/scan.py sections
    ```

1. Your screen will now show something similar to this:

    ```
    1: 3D
    2: 4K
    3: Foreign
    4: Hollywood
    5: Kids
    6: TV
    ```
  
    _Note: If you get an error here, see the [[FAQ|FAQ#fix-permission-issues-with-plex-logs]] on how to fix permissions._

1. The list here shows your section IDs in the format of `SECTION ID: LIBRARY NAME`. Note: Your section IDs may be different as it is based on the order you added them in Plex.
