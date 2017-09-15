## General Info

It is recommended to assign all your disk space to `/`, as all of your imported media and app data will be saved to `/mnt/local` and `/opt`,  respectively.

Downloads (i.e. NZBGet, ruTorrent) are stored in `~/downloads`, however, this can be changed to point to an extra disk by editing the [[setting.yml|Configuring-Settings]] file.

Note: All folders/paths are **case sensitive**. 


## Google Drive Paths


| Path                   | Purpose                                                                                                                                                            |
|:---------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <pre>/Media</pre>     | <pre> Location of the `Movies` and `TV` folders   </pre>                                                                                                                         |
| <pre>/Media/Movies</pre> | <pre> Location of all your movies. Each one within it's own folder. Preferably, in the format of `Movie Name (YEAR)` </pre>                                                                                                  |
| <pre>/Media/TV</pre>   | <pre> Location of all your TV shows. Each one within it's own folder. Individual season folders within those. </pre> |

_Note: These folders are not meant to be changed. However, if you would like to separate content into multiple libraries in Plex, you may do so by creating sub-folders within the `Movies` and `TV` folders (see [[Customizing Plex Libraries]] for more info)._


## Local Paths

### Media


| Path                   | Purpose                                                                                                                                                            |
|:---------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <pre>/mnt/local/Media</pre>     | <pre> Sonarr/Radarr imports will go here   </pre>                                                                                                                         |
| <pre>/mnt/plexdrive/Media</pre> | <pre> Media that is stored on Google Drive is mounted here (by Plexdrive) </pre>                                                                                                  |
| <pre>/mnt/unionfs/Media</pre>   | <pre> Combined folder of local media (/mnt/local/Media) and online media  (/mnt/plexdrive/Media). This is the folder Plex, Sonarr, and Radarr when scanning for media </pre> |

Note: Make sure `/mnt/local` has enough space to store the imported media.

### UnionFS_Cleaner


| Path               | Purpose                                                                                                                                                                                       |
|:------------------ |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <pre>/mnt/local/Media</pre> | <pre> Size of the local media folder is checked periodically. When the folder size reaches it's threshold (default 250GB), it will move that content to Google Drive, freeing up local disk space </pre> |





## Docker Paths

Note: It is advised to leave at least 100GB free on `/opt` for the docker data (see below).

### Plex

| Docker Path    | Host Path                   | Purpose                      |
|:-------------- |:--------------------------- |:---------------------------- |
| <pre>/data/Movies</pre> | <pre>/mnt/unionfs/Media/Movies</pre> | <pre> Plex reads this for Movies </pre>  |
| <pre>/data/TV</pre>     | <pre>/mnt/unionfs/Media/TV</pre>     | <pre> Plex reads this for TV Shows </pre>|


### Sonarr


| Docker Path            | Host Path                         | Purpose                                                                 |
|:---------------------- |:--------------------------------- |:----------------------------------------------------------------------- |
| <pre>/tv</pre>                  | <pre>/mnt/unionfs/Media/TV</pre>           | <pre> Sonarr will import to /tv which in turn is that folder on host system </pre> |
| <pre>/downloads/rutorrent</pre> | <pre>~/downloads/rutorrent (default) </pre> | <pre> ruTorrent download folder as set in settings.yml </pre>                       |
| <pre>/downloads/nzbget</pre>    | <pre>~/downloads/nzbget (default)   </pre> | <pre> NZBGet download folder as set in settings.yml </pre>                          |


### Radarr


| Docker Path            | Host Path                         | Purpose                                                                     |
|:---------------------- |:--------------------------------- |:--------------------------------------------------------------------------- |
| <pre>/movies</pre>              | <pre>/mnt/unionfs/Media/Movies</pre>       | <pre> Radarr will import to /movies which in turn is that folder on host system </pre> |
| <pre>/downloads/rutorrent</pre> | <pre>~/downloads/rutorrent (default) </pre> | <pre> ruTorrent download folder as set in settings.yml  </pre>                          |
| <pre>/downloads/nzbget</pre>    | <pre>~/downloads/nzbget (default) </pre>   | <pre> NZBGet download folder as set in settings.yml </pre>                               |


### PlexPy


| Docker Path | Host Path                                                      | Purpose                               |
|:----------- |:-------------------------------------------------------------- |:------------------------------------- |
| <pre>/logs</pre>     | <pre>/opt/plex/Library/Application Support/Plex Media Server/Logs</pre> | <pre> Location of Plex logs; used by PlexPy </pre> |
