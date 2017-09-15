## Obtaining the Plex Autoscan URL

This will be used later by Sonarr/Radarr.

1. On the server's shell, run the following command:

    ```
    cat /opt/plex_autoscan/*.log | grep http
    ```
1. Copy the link you find here (which will look like `http://0.0.0.0:3468/PLEXAUTOSCANAPI`).

1. Replace "0.0.0.0" with "plex._yourdomain.com_" (i.e. http://plex._yourdomain.com_:3468/PLEXAUTOSCANAPI).


## Adding Plex Access Token into Plex Autoscan

1. Retrieving a Plex Access Token

    1. via Bookmarklet
        1. Go to https://github.com/jacobwgillespie/plex-token-bookmarklet and simply drag the bookmarlet into bookmarks bar of your browser. 

            -  You can also just manually create a bookmark and pasting in the following address:

                 ```
                 javascript:(function()%7Bif%20(%2F(%5E%7C%5C.)plex%5C.tv%24%2F.test(window.location.hostname))%20%7Bprompt('Your%20Plex%20token'%2C%20window.PLEXWEB.myPlexAccessToken%7C%7Cwindow.localStorage.myPlexAccessToken)%7D%20else%20%7Balert('Please%20drag%20this%20link%20to%20your%20bookmark%20bar%20and%20click%20it%20when%20using%20the%20Plex%20Web%20App')%3B%7D%7D)()
                 ```

         1.  Go to http://plex.tv/web and login. Click on the bookmarklet to obtain a Plex Access Token.

1. Adding the Plex Access Token in to Plex Autoscan config.

 1. On the server's shell, run the following command:

     ```
     nano /opt/plex_autoscan/config/config.json
     ```
 1. Add the Plex Access Token to `"PLEX_TOKEN":` so that it now appears as `"PLEX_TOKEN": "xxxxxxxxxxxxxx",`.

   1. Note: Make sure it is within the quotes (`"`) and there is a comma (`,`) after it.

 1. `ctrl-x` and `y` to save.
