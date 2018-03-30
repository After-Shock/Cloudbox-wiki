[Plex Dupefinder](https://github.com/l3uddz/plex_dupefinder/) (by [l3uddz](https://github.com/l3uddz/)) is a script that finds duplicate versions of media (TV episodes and movies) in your Plex Library and tells Plex to remove the lowest quality versions (based on a scoring algorithm), either automatically or interactively (i.e. with a prompt on each find), leaving you with one high quality media file. 

The scoring is based on: non-configurable and configurable parameters.

  - Non-configurable parameters are: _bitrate_, _duration_, _resolution_, _audio channel_, and _file size_. 

  - Configurable parameters are: _codec scores_ and _filename scores_.

_Note: For Feederbox/Plexbox setups, all the commands below will be done on the Plexbox._


# First Time Setup


## 1. Install Plex Dupefinder

- Run the following commands: 

  ```bash
  cd ~/cloudbox/
  sudo ansible-playbook cloudbox.yml --tags install-plex_dupefinder
  ```

## 2. Plex Dupefinder Config

### Sample:

```json
{
  "AUTO_DELETE": false,
  "CODEC_SCORES": {
    "Unknown": 0,
    "aac": 1000,
    "ac3": 1000,
    "dca": 2000,
    "dca-ma": 4000,
    "eac3": 1250,
    "flac": 2500,
    "mp2": 500,
    "mp3": 1000,
    "pcm": 2500,
    "truehd": 4500,
    "wmapro": 200
  },
  "FILENAME_SCORES": {
    "*Remux*": 20000,
    "*1080p*BluRay*": 15000,
    "*720p*BluRay*": 10000,
    "*WEB*NTB*": 5000,
    "*WEB*VISUM*": 5000,
    "*WEB*KINGS*": 5000,
    "*WEB*CasStudio*": 5000,
    "*WEB*SiGMA*": 5000,
    "*WEB*QOQ*": 5000,
    "*WEB*TROLLHD*": 2500,
    "*WEB*TBS*": -1000,
    "*HDTV*": -1000,
    "*dvd*": -1000,
    "*.avi": -1000,
    "*.ts": -1000,
    "*.vob": -5000
  },
  "PLEX_SECTIONS": {
    "Movies": 1,
    "TV": 2
  },
  "PLEX_SERVER": "https://plex.domain.com",
  "PLEX_TOKEN": "",
  "SKIP_LIST": [],
  "SCORE_FILESIZE": true
}
```

### 1. Edit config.json

- Run the following command: 

   ```bash
   nano /opt/plex_dupefinder/config.json
   ```

 - Note: Make sure all edits are within quotes (`"`) and there is a comma (`,`) after it (all except the last one).


### 2. Auto Delete

- Under `AUTO_DELETE`, set your desired option.

  - `"AUTO_DELETE": true,`  - Plex Dupefinder will run in automatic mode.

  - `"AUTO_DELETE": false,` -  Plex Dupefinder will run in interactive mode. (Default)

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

### 3. Codec Scoring (Optional)

- You can set `CODEC_SCORES` to your preference. However, default settings should be sufficient for most. 


### 4. Filename Scoring (Optional)

- You can set `FILENAME_SCORES` to your preference. However, default settings should be sufficient for most. 


### 5. Plex Library Sections

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

### 6. Plex Server URL

- Pre-filled with your Plex server's URL. 

### 7. Plex Token

1. Obtain a Plex Access Token: See [[Plex Token]].

2. Add the Plex Access Token to `"PLEX_TOKEN"` so that it now appears as `"PLEX_TOKEN": "xxxxxxxxxxxxxx",`.

      - Note: Make sure it is within the quotes (`"`) and there is a comma (`,`) after it.



### 8. Skip List (Optional)

- You can use `SKIP_LIST` to skip certain folders. 

- Example:

  ```json
  "SKIP_LIST": ["/4K-Movies/"]
  ```

### 9. Save config.json

- `Ctrl-x`, `y`, and `enter` to save.

## 3. Set "Allow media deletion" in Plex

1. Click the Settings icon (top right) -> "Server" (top) -> "Library" (left).

1. Set the following:
   - "Allow media deletion": `enabled`

1. Click "SAVE CHANGES".

    ![](http://i.imgur.com/D82n8vh.png)


## 4. Run Plex Dupefinder

- Simply run the following command: 

  ```
  plexdupes
  ```
