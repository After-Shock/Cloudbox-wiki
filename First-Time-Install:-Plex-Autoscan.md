Plex Autoscan comes preset with a default configuration as related to Cloudbox. However, there a few things that need to be set by you. 

_Note: If you would like to learn more about what Plex Autoscan does and all the options available, see https://github.com/l3uddz/plex_autoscan._


## 1. Retrieve a Plex Access Token

There are a few different ways to do this. Any of these will do. 

1. Using a script <a href="#note1" id="note1ref"><sup>[1]</sup></a> 


   1. On the server's shell, run the following command:

      ```bash
      /opt/scripts/plex/plex_token.sh
      ```
   
   1. You will be prompted to enter your Plex login and then presented with the Plex Access Token (under `Your X_PLEX_TOKEN:`)


1. Using a Bookmarklet <a href="#note2" id="note2ref"><sup>[2]</sup></a> 


   1. Go [[here|https://github.com/jacobwgillespie/plex-token-bookmarklet]] and drag the bookmarklet into the bookmarks bar of your browser. 

      -  You can also create a bookmark and paste in the following address:

         ```
         javascript:(function()%7Bif%20(%2F(%5E%7C%5C.)plex%5C.tv%24%2F.test(window.location.hostname))%20%7Bprompt('Your%20Plex%20token'%2C%20window.PLEXWEB.myPlexAccessToken%7C%7Cwindow.localStorage.myPlexAccessToken)%7D%20else%20%7Balert('Please%20drag%20this%20link%20to%20your%20bookmark%20bar%20and%20click%20it%20when%20using%20the%20Plex%20Web%20App')%3B%7D%7D)()
          ```

    1.  Go to http://plex.tv/web and login. Click on the bookmarklet to obtain a Plex Access Token.
   

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

The Plex Autoscan URL is needed during the setup of [[Sonarr|Sonarr#7-plex-autoscan]] and [[Radarr|Radarr#7-plex-autoscan]].


To get your Plex Autoscan URL, run the following command:

 ```shell
 /opt/scripts/plex_autoscan/plex_autoscan_url.sh
 ```

This will be in the format of `http://server_ip:server_port/server_pass`.



_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._


## 4. Upload a Blank Control File to Google Drive


```
cd ~/
touch mounted.bin
rclone -v move mounted.bin google:
```

_Note 1: If your Rclone remote config has a different name for Google Drive, replace `google:` with yours._

_Note 2: For explanation on the purpose of the control file, see the [[FAQ|FAQ#purpose-of-a-control-file-in-plex-autoscan]]_.




---

<sub>Credit:<br></sub>
<sub> <a id="note1" href="#note1ref"><sup>1</sup></a> https://github.com/wernight</sub><br>
<sub> <a id="note2" href="#note2ref"><sup>2</sup></a> https://github.com/jacobwgillespie</sub>
