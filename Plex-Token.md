The following guide will take you through obtaining a Plex Token for your Plex account.


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
   



---

<sub>Credit:<br></sub>
<sub> <a id="note1" href="#note1ref"><sup>1</sup></a> https://github.com/wernight</sub><br>
<sub> <a id="note2" href="#note2ref"><sup>2</sup></a> https://github.com/jacobwgillespie</sub>
