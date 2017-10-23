## 1. Obtaining the Plex Autoscan URL

The Plex Autoscan URL is needed during the setup of [[Sonarr|Sonarr#7-plex-autoscan]] and [[Radarr|Radarr#7-plex-autoscan]].


To get your Plex Autoscan URL, run the following command:

 ```shell
 /opt/scripts/plex_autoscan/plex_autoscan_url.sh
 ```

This will be in the format of `http://server_ip_address:port/token`.


_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._
       


## 2. Retrieving a Plex Access Token

There are a few different ways to do this. Any of these will do. 

1. Using a script <a href="#note1" id="note1ref"><sup>[1]</sup></a> 


   1. On the server's shell, run the following command:

      ```bash
      /opt/scripts/plex/plex_token.sh
      ```
   
   1. You will be prompted to enter your Plex login and then presented with the  Plex Access Token (under `Your X_PLEX_TOKEN:`)


1. Using a Bookmarklet <a href="#note2" id="note2ref"><sup>[2]</sup></a> 


   1. Go to https://github.com/jacobwgillespie/plex-token-bookmarklet and simply drag the bookmarlet into bookmarks bar of your browser. 

      -  You can also just manually create a bookmark and pasting in the following address:

         ```
         javascript:(function()%7Bif%20(%2F(%5E%7C%5C.)plex%5C.tv%24%2F.test(window.location.hostname))%20%7Bprompt('Your%20Plex%20token'%2C%20window.PLEXWEB.myPlexAccessToken%7C%7Cwindow.localStorage.myPlexAccessToken)%7D%20else%20%7Balert('Please%20drag%20this%20link%20to%20your%20bookmark%20bar%20and%20click%20it%20when%20using%20the%20Plex%20Web%20App')%3B%7D%7D)()
          ```

    1.  Go to http://plex.tv/web and login. Click on the bookmarklet to obtain a Plex Access Token.
   

## 3. Adding Plex Access Token into Plex Autoscan

   1. On the server's shell, run the following command:

      ```
      nano /opt/plex_autoscan/config/config.json
      ```
   1. Add the Plex Access Token to `"PLEX_TOKEN":` so that it now appears as `"PLEX_TOKEN": "xxxxxxxxxxxxxx",`.

      - Note: Make sure it is within the quotes (`"`) and there is a comma (`,`) after it.

   1. `ctrl-x` and `y` to save.


---

Credit:
 
<sub> <a id="note1" href="#note1ref"><sup>1</sup></a> https://github.com/wernight/docker-plex-media-server</sub>

 <sub> <a id="note2" href="#note2ref"><sup>2</sup></a> https://github.com/jacobwgillespie</sub>
