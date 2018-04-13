[Plex Autoscan](https://github.com/l3uddz/plex_autoscan/) (by [l3uddz](https://github.com/l3uddz/)) is a script that assists Plex with the adding media files that were imported by Sonarr / Radarr, by only scanning the folder that has been imported (vs the entire section library folder), thereby preventing Google API bans. 

Plex Autoscan comes configured out of the box (as related to Cloudbox). However, there a few things that need to be set by you. 

_Note: If you would like to learn more about what Plex Autoscan does and all the options available, see https://github.com/l3uddz/plex_autoscan._


## 1. Obtain a Plex Access Token

 - See the [[Plex Token]] page.

## 2. Add the Plex Access Token into Plex Autoscan

   1. On the server's shell, run the following command:

      ```
      nano /opt/plex_autoscan/config/config.json
      ```
   1. Add the Plex Access Token to `"PLEX_TOKEN":` so that it now appears as `"PLEX_TOKEN": "xxxxxxxxxxxxxx",`.

      - Note: Make sure it is within the quotes (`"`) and there is a comma (`,`) after it.

   1. `Ctrl-x`, `y`, and `enter` to save.

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._


## 3. Obtaining the Plex Autoscan URL

The Plex Autoscan URL is needed during the setup of [[Sonarr|First-Time-Install: Sonarr#7-plex-autoscan]] and [[Radarr|First-Time-Install: Radarr#7-plex-autoscan]].


To get your Plex Autoscan URL, run the following command:

 ```shell
 /opt/scripts/plex_autoscan/plex_autoscan_url.sh
 ```

This will be in the format of:

```
http://server_ip:plex_autoscan_port/plex_autoscan_pass

eg. http://1.2.3.4:3468/aiG7Uwie9iodTTlaisahcieNaeVonu6I
```

(New script uses `http://plex.domain.com:plex_autoscan_port/plex_autoscan_pass` format). 



_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._


## 4. Upload a Blank Control File to Google Drive


```
rclone touch google:/mounted.bin
```

_Note 1: If your Rclone remote config has a different name for Google Drive, replace `google:` with yours._

_Note 2: Above command requires Rclone version 1.39 or higher._

_Note 3: For explanation on the purpose of the control file, see the [[FAQ|FAQ#purpose-of-a-control-file-in-plex-autoscan]]_.




---

<sub>Credit:<br></sub>
<sub> <a id="note1" href="#note1ref"><sup>1</sup></a> https://github.com/wernight</sub><br>
<sub> <a id="note2" href="#note2ref"><sup>2</sup></a> https://github.com/jacobwgillespie</sub>
