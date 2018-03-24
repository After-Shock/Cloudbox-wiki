Plex Dupefinder (by l3uddz) is a script that finds duplicate versions of media (TV episodes and movies) in your Plex Library and tells Plex to remove the lowest quality versions (based on a scoring algorithm), either automatically or interactively (i.e. with a prompt on each find), leaving you with one high quality media file. 

The scoring is based on: `codec_scores` (configurable), `bitrate`, `duration`, `width/height`, `audio channels`, and `file size`. 

## 2. First Time Setup

### 1. Install Plex Dupefinder

- Run the following commands: 

  ```bash
  cd ~/cloudbox/
  sudo ansible-playbook cloudbox.yml --tags install-plex_dupefinder
  ```

  _Note: For Feederbox/Plexbox setups, this will be done on the Plexbox._

## 2. Add Plex Token to config.json

1. On the server's shell, run the following command:

    ```
    nano /opt/plex_dupefinder/config.json
    ```

1. Scroll down to the `PLEX_SECTION_PATH_MAPPINGS` section.

    1. Under this section, you will need to add your section IDs and the library paths (as located within the `/Media` folder in Google Drive). 

       The format will look like:

       ```json
       "SECTION_NUMBER": [
           "/Movies/<folderpath>/"
       ],
       ```

       Note 1: Make sure the folder paths are within quotes (e.g. `"/Movies/3D"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

       Note 2: Since folders are case sensitive, make sure the folder path matches the same case as the folders you created in Google Drive (e.g. `"/Movies/4K"` is not the same as `"/Movies/4k"`).

    1. After the changes, the section will now look similar to this:

       ```json
       "PLEX_SECTION_PATH_MAPPINGS": {
          "1": [
              "/Movies/3D/"
          ],
          "2": [
              "/Movies/4K/"
          ],
          "3": [
              "/Movies/Foreign/"
          ],
          "4": [
              "/Movies/Hollywood/"
          ],
          "5": [
              "/Movies/Kids/"
          ],
          "6": [
              "/TV/"
          ]
       },
       ```

1. `Ctrl-x`, `y`, and `enter` to save.


1. Restart Plex Autoscan: `sudo systemctl restart plex_autoscan`
