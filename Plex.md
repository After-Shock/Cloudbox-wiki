so they visit plex.domain.com
login
then in server list, click the new server that popped up
they will see this greet screen
click got it
put their new server name
click next next done




go to settings
server
then go to remote access
then tick the manual public port, and enter 32400
click Retry

library tab
empty trash automatically after ervery scan, and allow media deletion is turned off
turn generate chpater thumbnails to never
save changes

go to network
disable local network discovery
save changes

transcoder
set transcode duration to 150
and the buffer to 600
save
dlna, turn off timeline reporting and save


scheduled tasks, turn off upgrade media analysis during mainteance, turn off extensive media analysis during maintenance, turn off refresh of program guide data and analkyse tag photos turn off
then save

![](https://imgur.com/xp5JUtQ)


extras, turn off include cinema trailers
once that is done

Note: order is important or else unionfs_cleaner config will need to be updated to reflect section id changes. 

add the Movies library
name it Movies
then Click add folder
the folder is /data/Movies
once its in the box
click Advanced
turn off, Enable cinema trailers, turn off video preview thumbnails, turn off find trailers and extras automatically then click Add library

click add library, then shows, name it TV, choose the /data/TV folder
once its in the box
click Advanced
turn off, Enable cinema trailers, turn off video preview thumbnails, turn off find trailers and extras automatically then click Add library


