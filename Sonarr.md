first they go to settings -> general and change the branch to develop for sonarr
set the authentication and a username and password




media management:
enable rename episodes
untick analyse video files 
untick use hardlinks instead of copy

download client:
enable remove on completed download handeling

Add download client. 
host: nzbget
username and password your previously set.
category: `sonarr` (lowercase)


rutorrent:
host: rutorrent
port: 80
username and pass you set in settings.yml on install
category sonarr.
test it, it will fail the first time, then test again and it will succeed.