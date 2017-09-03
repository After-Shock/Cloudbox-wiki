### Paths

/mnt/local = local content - sonarr/radarr imports will go here.
/mnt/plexdrive = google drive content (plexdrive)
/mnt/unionfs = combined folder of /mnt/local and /mnt/unionfs.

Docker paths:

plex:

/data/Movies = /mnt/unionfs/Media/Movies on host system
/data/TV = mnt/unionfs/Media/TV on host system.

sonarr:

/tv = /mnt/unionfs/Media/TV on host system (sonarr will import to /tv which in turn is that folder on host system)
/downloads/rutorrent = rutorrent download folder set in settings.yml (default: ~/downloads/rutorrent)
/downloads/nzbget = same as above (default: ~/downloads/nzbget)

radarr:

/movies = /mnt/unionfs/Media/Movies on host system (sonarr will import to /movies which in turn is that folder on host system)
/downloads/rutorrent = rutorrent download folder set in settings.yml (default: ~/downloads/rutorrent)
/downloads/nzbget = same as above (default: ~/downloads/nzbget)

plexpy:

logs folder for plex is /logs - which in reality is /opt/plex/Library/Application Support/Plex Media Server/Logs on the host system.

unionfs_cleaner:

unionfs_cleaner by default checks the size of /mnt/local/Media - when size reaches threshhold, (default 250gb) it will move that content to google, freeing up the space.

image workflow:

http://i.imgur.com/xVR28pn.png


