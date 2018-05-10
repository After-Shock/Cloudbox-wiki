[Plex Dupefinder](https://github.com/l3uddz/plex_dupefinder/) (by [l3uddz](https://github.com/l3uddz/)) is a script that finds duplicate versions of media (TV episodes and movies) in your Plex Library and tells Plex to remove the lowest quality versions (based on a scoring algorithm), either automatically or interactively (i.e. with a prompt on each find), leaving you with one high quality media file. 

![](https://i.imgur.com/d1sDNlE.png)


_Note: For Feederbox/Plexbox setups, this can be install in either system._ 


The scoring is based on: non-configurable and configurable parameters.

  - Non-configurable parameters are: _bitrate_, _duration_, _height_, _width_, and _audio channel_.

  - Configurable parameters are: _audio codec scores_, _video codec scores_, _video resolution scores_, _filename scores_, and _file sizes_ (can only be toggled on or off).

  - Note: bitrate, duration, height, width, audio channel, audio and video codecs, video resolutions (e.g. SD, 480p, 720p, 1080p, 4K, etc), and file sizes are all taken from the metadata Plex retrieves during media analysis.

---
# Demo 

[![asciicast](https://asciinema.org/a/180157.png)](https://asciinema.org/a/180157)


# First Time Setup


## 1. Install Plex Dupefinder

Run the following commands: 

  ```bash
  cd ~/cloudbox/
  sudo ansible-playbook cloudbox.yml --tags install-plex_dupefinder
  ```

## 2. Plex Dupefinder Config

### Sample:

```json
{
  "AUDIO_CODEC_SCORES": {
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
    "wmapro": 200,
    "Unknown": 0
  },
  "AUTO_DELETE": false,
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
    "*REPACK*": 1500,
    "*PROPER*": 1500,
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
  "PLEX_SERVER": "https://plex.yourdomain.com",
  "PLEX_TOKEN": "",
  "SCORE_FILESIZE": true,
  "SKIP_LIST": [],
  "VIDEO_CODEC_SCORES": {
    "h264": 10000,
    "h265": 5000,
    "hevc": 5000,
    "mpeg1video": 250,
    "mpeg2video": 250,
    "mpeg4": 500,
    "msmpeg4": 100,
    "msmpeg4v2": 100,
    "msmpeg4v3": 100,
    "vc1": 3000,
    "vp9": 1000,
    "wmv2": 250,
    "wmv3": 250,
    "Unknown": 0
  },
  "VIDEO_RESOLUTION_SCORES": {
    "4k": 20000,
    "1080": 10000,
    "720": 5000,
    "480": 3000,
    "sd": 1000,
    "Unknown": 0
  }
}

```

### 1. Edit config.json

- Run the following command: 

   ```bash
   nano /opt/plex_dupefinder/config.json
   ```

 - Note: Make sure all edits are within quotes (`"`) and there is a comma (`,`) after it (all except the last one).

### 2. Audio Codec Scores (Optional)

- You can set `AUDIO_CODEC_SCORES` to your preference. However, default settings should be sufficient for most. 


### 3. Auto Delete

- Under `AUTO_DELETE`, set your desired option.

  - `"AUTO_DELETE": true,`  - Plex Dupefinder will run in automatic mode.

  - `"AUTO_DELETE": false,` -  Plex Dupefinder will run in interactive mode. (Default)

    - Options: 

      - Skip (i.e. keep both): `0`

      - Choose the best one (and delete the rest): `b`

      - Select the item to keep (and delete the rest): `#` (i.e. `1`, `2`, `3`, etc).
 



### 4. Filename Scores (Optional)

- You can set `FILENAME_SCORES` to your preference. However, default settings should be sufficient for most. 


### 5. Plex Library Sections

1. Go to Plex and get all the names of your Plex Libraries you want to find duplicates in.

   - Example Library:
   
     ![](https://i.imgur.com/JFRTD1m.png)

1. Under `PLEX_SECTIONS`, type in the Plex *Library Name* (exactly) and specify the *Library Type* (_not the Section ID_): `1` for movies or `2` for TV shows. 

   - Format: 

     ```
     "PLEX_SECTIONS": {
       "LIBRARY_NAME_1": #,
       "LIBRARY_NAME_2": #
     },
     ```
     \# = Library Type: `1` or `2`

   - For basic libraries, this will look like: 

     ```json
     "PLEX_SECTIONS": {
       "Movies": 1,
       "TV": 2
     },
     ```

   - For more advanced libraries (e.g. [[Customizing Plex Libraries]]), this will look like: 

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

1. Obtain a Plex Access Token: See [[Plex Access Token]].

2. Add the Plex Access Token to `"PLEX_TOKEN"` so that it now appears as `"PLEX_TOKEN": "xxxxxxxxxxxxxx",`.

      - Note: Make sure it is within the quotes (`"`) and there is a comma (`,`) after it.

### 8. Filesize Scores (Optional)

- `"SCORE_FILESIZE": true` will add more points to the overall score based on the actual file size. ]

-  Note: In some situations (e.g. a bad encode resulting in a large size), this may be something you want to turn it off (`false`). However, the default settings (i.e. `true`) should be sufficient for most. 


### 9. Skip List (Optional)

- In Auto Delete mode, any file paths matching the patterns (i.e folders), listed in `SKIP_LIST`, will be ignored.

- Example:

  ```json
  "SKIP_LIST": ["/Movies4K/"]
  ```

### 10. Video Codec Scores (Optional)

- You can set `VIDEO_CODEC_SCORES` to your preference. However, default settings should be sufficient for most. 

### 11. Video Resolution Scoring (Optional)

- You can set `VIDEO_RESOLUTION_SCORES` to your preference. However, default settings should be sufficient for most. 


### 12. Save config.json

- `Ctrl-x`, `y`, and `enter` to save.

## 3. Set "Allow media deletion" in Plex

1. In Plex, click the Settings icon (top right) -> "Server" (top) -> "Library" (left).

1. Set the following:
   - "Allow media deletion": `enabled`

1. Click "SAVE CHANGES".

    ![](http://i.imgur.com/D82n8vh.png)


## 4. Run Plex Dupefinder

- Simply run the following command: 

  ```
  plexdupes
  ```