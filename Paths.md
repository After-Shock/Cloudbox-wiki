## General Info

It is recommended to assign all your disk space to <pre>/</pre>, as all of your imported media and app data will be saved to <pre>/mnt/local</pre> and <pre>/opt</pre>,  respectively.

Downloads (i.e. NZBGet, ruTorrent) are stored in <pre>~/downloads</pre>, however, this can be changed to point to an extra disk by editing the [[setting.yml|Configuring-Settings]] file.

## Local Paths

### Media


| Path                   | Purpose                                                                                                                                                            |
|:---------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <pre>/mnt/local/Media</pre>     | Sonarr/Radarr imports will go here  here                                                                                                                           |
| <pre>/mnt/plexdrive/Media</pre> | Media that is stored on Google Drive is mounted here (by Plexdrive)                                                                                                   |
| <pre>/mnt/unionfs/Media</pre>   | Combined folder of local media (<pre>/mnt/local/Media</pre>) and online media (<pre>/mnt/plexdrive/Media</pre>). This is the folder Plex, Sonarr, and Radarr when scanning for media |

Note: Make sure <pre>/mnt/local</pre> has enough space to store the imported media.

### UnionFS_Cleaner


| Path               | Purpose                                                                                                                                                                                       |
|:------------------ |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <pre>/mnt/local/Media</pre> | Size of the local media folder is checked periodically. When the folder size reaches it's threshold (default `250GB`), it will move that content to Google Drive, freeing up local disk space |





## Docker Paths

Note: It is advised to leave at least 100GB free on `/opt` for the docker data (see below).

### Plex

| Docker Path    | Host Path                   | Purpose                      |
|:-------------- |:--------------------------- |:---------------------------- |
| <pre>/data/Movies</pre> | <pre>/mnt/unionfs/Media/Movies</pre> | Plex reads this for Movies   |
| <pre>/data/TV</pre>     | <pre>/mnt/unionfs/Media/TV</pre>     | Plex reads this for TV Shows |


### Sonarr


| Docker Path            | Host Path                         | Purpose                                                                 |
|:---------------------- |:--------------------------------- |:----------------------------------------------------------------------- |
| <pre>/tv</pre>                  | <pre>/mnt/unionfs/Media/TV</pre>           | Sonarr will import to <pre>/tv</pre> which in turn is that folder on host system |
| <pre>/downloads/rutorrent</pre> | <pre>~/downloads/rutorrent</pre> (default) | ruTorrent download folder as set in settings.yml                        |
| <pre>/downloads/nzbget</pre>    | <pre>~/downloads/nzbget</pre> (default)    | NZBGet download folder as set in settings.yml                           |


### Radarr


| Docker Path            | Host Path                         | Purpose                                                                     |
|:---------------------- |:--------------------------------- |:--------------------------------------------------------------------------- |
| <pre>/movies</pre>              | <pre>/mnt/unionfs/Media/Movies</pre>       | Radarr will import to <pre>/movies</pre> which in turn is that folder on host system |
| <pre>/downloads/rutorrent</pre> | <pre>~/downloads/rutorrent</pre> (default) | ruTorrent download folder as set in settings.yml                            |
| <pre>/downloads/nzbget</pre>    | <pre>~/downloads/nzbget</pre> (default)    | NZBGet download folder as set in settings.yml                               |


### PlexPy


| Docker Path | Host Path                                                      | Purpose                               |
|:----------- |:-------------------------------------------------------------- |:------------------------------------- |
| <pre>/logs</pre>     | <pre>/opt/plex/Library/Application Support/Plex Media Server/Logs</pre> | Location of Plex logs; used by PlexPy |
