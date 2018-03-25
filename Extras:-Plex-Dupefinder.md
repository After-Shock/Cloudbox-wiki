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

- Under `AUTO_DELETE`, set your desired option.

  - `"AUTO_DELETE": true,`  - Plex Dupefinder will run in automatic mode.

  - `"AUTO_DELETE": false,` - Default. Plex Dupefinder will run in interactive mode.

    - Options: 

      - Skip (i.e. keep both): `0`

      - Keep just one: `ID of item to keep`

      ```
      Initialized
      Finding dupes...
      Found 58 dupes for section 'Movies'
      Which media item do you wish to keep for b'Silverado'
      	ID: 23523 - Score: 142244 - INFO: {'id': 23523, 'video_codec': 'h264', 'score': 142244, 'file': [b'/data/Movies/Movies/Silverado (1985)/Silverado.1985.1080p.BluRay.x264-BLADE.mkv'], 'audio_channels': 6, 'video_duration': 61381, 'video_resolution': '1080', 'show_key': '/library/metadata/22256', 'video_width': 1920, 'video_bitrate': 15274, 'video_height': 800, 'audio_codec': 'ac3', 'multipart': False, 'file_size': 117189341}
      	ID: 271700 - Score: 9417944 - INFO: {'id': 271700, 'video_codec': 'h264', 'score': 9417944, 'file': [b'/data/Movies/Movies/Silverado (1985)/Silverado.1985.1080p.BluRay.x264-CINEFILE.mkv'], 'audio_channels': 6, 'video_duration': 7956960, 'video_resolution': '1080', 'show_key': '/library/metadata/22256', 'video_width': 1920, 'video_bitrate': 9442, 'video_height': 800, 'audio_codec': 'ac3', 'multipart': False, 'file_size': 9390825514}
      Enter ID of item to keep (0 = skip):
      ```


### 2. Add Plex Libraries

1. Get all the names of your Plex Libraries you want to search de-dupe. 

   - Example Library:
   
     ![](https://i.imgur.com/JFRTD1m.png)

1. Under `PLEX_SECTIONS`, type in your library names and specify `1` for movies or `2` for TV shows. 

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

### 4. Set Scoring (optional)

- You can set `CODEC_SCORES` to your preference.

### 5. Skip List (optional)

- You can use `SKIP_LIST` to skip certain paths. 

- Example:

  ```json
  "SKIP_LIST": ["/4K-Movies/"]
  ```


### 6. Saving config.json

- `Ctrl-x`, `y`, and `enter` to save.