If in Plex step, moves was not first and tv second...

/opt/plex_autoscan/scan.py sections


nano /opt/plex_autoscan/config/config.json
switch the id numbers
systemctl restart plex_autoscan


    <h1>Plex Token Bookmarklet</h1>

Create a new bookmark called `Plex Access Token` in the Bookmark Bar of your browser. Paste the following into location:
 ```
javascript:(function()%7Bif%20(%2F(%5E%7C%5C.)plex%5C.tv%24%2F.test(window.location.hostname))%20%7Bprompt('Your%20Plex%20token'%2C%20window.PLEXWEB.myPlexAccessToken%7C%7Cwindow.localStorage.myPlexAccessToken)%7D%20else%20%7Balert('Please%20drag%20this%20link%20to%20your%20bookmark%20bar%20and%20click%20it%20when%20using%20the%20Plex%20Web%20App')%3B%7D%7D)()
``` 

Source: https://github.com/jacobwgillespie/plex-token-bookmarklet