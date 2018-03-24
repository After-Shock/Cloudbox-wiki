Plex Dupefinder (by l3uddz) is a script that finds duplicate versions of media (TV episodes and movies) in your Plex Library and tells Plex to remove the lowest quality versions (based on a scoring algorithm), either automatically or interactively (ie with a prompt on each find), leaving you with one high quality media file. 

The scoring is based on: `codec_scores` (configurable), `bitrate`, `duration`, `width/height`, `audio channels`, and `file size`. 

## 2. First Time Setup

### 2. Install Plex Dupefinder

- Run the following commands: 

  ```bash
  cd ~/cloudbox/
  sudo ansible-playbook cloudbox.yml --tags install-plex_dupefinder
  ```