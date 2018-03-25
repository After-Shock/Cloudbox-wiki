Plex Dupefinder (by [l3uddz](https://github.com/l3uddz/plex_dupefinder/)) is a script that finds duplicate versions of media (TV episodes and movies) in your Plex Library and tells Plex to remove the lowest quality versions (based on a scoring algorithm), either automatically or interactively (i.e. with a prompt on each find), leaving you with one high quality media file. 

The scoring is based on: `codec_scores` (configurable), `bitrate`, `duration`, `resolution`, `audio channels`, and `file size`. 

_Note: For Feederbox/Plexbox setups, all the commands below will be done on the Plexbox._


# First Time Setup

## 1. Install Plex Dupefinder

- Run the following commands: 

  ```bash
  cd ~/cloudbox/
  sudo ansible-playbook cloudbox.yml --tags install-plex_dupefinder
  ```

## 2. Plex Dupefinder Config

### 1. Editing config.json

- Run the following command: 

   ```bash
   nano /opt/plex_dupefinder/config.json
   ```

 - Note: Make sure all edits are within quotes (`"`) and there is a comma (`,`) after it (all except the last one).


### 2. Set Autodelete option

- Under `"AUTO_DELETE"`, set your desired option.

  -  `"AUTO_DELETE": false,` - Default. Plex Dupefinder will give you a prompt 

### 2. Add Plex Libraries

1. Get all the names of your Plex Libraries you want to search de-dupe. 

   ![](https://i.imgur.com/JFRTD1m.png)

1. Under `"PLEX_SECTIONS"`, type in your library names and specify `1` for movies or `2` for TV shows. 

   - For basic libraries, it will look like this: 

     ```json
     "PLEX_SECTIONS": {
       "Movies": 1,
       "TV": 2
     },
     ```

   - For more advanced libraries (e.g. [[Customizing Plex Libraries]]), it will look like this: 

     ```json
     "PLEX_SECTIONS": {
        "3D": 1,
        "4K": 1,
        "Foreign": 1,
        "Hollywood": 1,
        "Kids": 1,
        "TV": 2
     },
     ```

### 3. Add Plex Token

1. Obtain a Plex Access Token: See [[Plex Token]].

2. Add the Plex Access Token to `"PLEX_TOKEN"` so that it now appears as `"PLEX_TOKEN": "xxxxxxxxxxxxxx",`.

      - Note: Make sure it is within the quotes (`"`) and there is a comma (`,`) after it.






#### 1. Retrieve Plex Section IDs and Library Names

 - See the [[Plex Token]] page.


#### 2. Modify Plex Dupefinder config

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._

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
