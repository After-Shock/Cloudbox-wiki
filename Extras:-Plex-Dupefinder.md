Plex Dupefinder (by l3uddz) is a script that finds duplicate versions of media (TV episodes and movies) in your Plex Library and tells Plex to remove the lowest quality versions (based on a scoring algorithm), either automatically or interactively (i.e. with a prompt on each find), leaving you with one high quality media file. 

The scoring is based on: `codec_scores` (configurable), `bitrate`, `duration`, `resolution`, `audio channels`, and `file size`. 

# First Time Setup

## 1. Install Plex Dupefinder

- Run the following commands: 

  ```bash
  cd ~/cloudbox/
  sudo ansible-playbook cloudbox.yml --tags install-plex_dupefinder
  ```

  _Note: For Feederbox/Plexbox setups, this will be done on the Plexbox._

## 2. Add a Plex Token

### 1. Obtain a Plex Access Token

 - See [[Plex Token]].

### 2. Add the Plex Access Token into Plex Dupefinder config

   1. On the server's shell, run the following command:

      ```
      nano /opt/plex_dupefinder/config.json
      ```
   1. Add the Plex Access Token to `"PLEX_TOKEN":` so that it now appears as `"PLEX_TOKEN": "xxxxxxxxxxxxxx",`.

      - Note: Make sure it is within the quotes (`"`) and there is a comma (`,`) after it.

   1. `Ctrl-x`, `y`, and `enter` to save.


