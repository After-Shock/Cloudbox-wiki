## General Info

It is recommended to assign all your disk space to `/`, as all of your imported media and app data will be saved to `/mnt/local` and `/opt`,  respectively.


Note 1: **ALL** folders/paths mentioned below, and elsewhere on the wiki, are **CASE SENSITIVE** (e.g. Google Drive: `Media` not `media`, `Movies` not `movies`, `TV` not `tv`; Plex Requests: `/logs` not `/Logs`, etc). This is important or else apps like Plex, Sonarr, and Radarr would not be able find your media files.

Note 2: This wiki uses `~/` interchangeably with `/home/<username>/` (defined as `/home/{{user}}/` in [[settings.yml|Configuring-Settings]]}. So if your user name was `seed`, your `~/` path would be the same as `/home/seed/`.

## Google Drive Paths


| Path                   | Purpose                                                                                                                                                            |
|:---------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <pre>/Media</pre>     | <pre> Location of the `Movies` and `TV` folders   </pre>                                                                                                                         |
| <pre>/Media/Movies</pre> | <pre> Location of all your movies (folder format: /Media/Movies/Movie Name (year)/movie file.ext) </pre>                                                                                                  |
| <pre>/Media/TV</pre>   | <pre> Location of all your TV shows (folder format: /Media/TV/TV Show Name/Season 00/episode file.ext)</pre> |

_Note: If you would like to customize your Plex libraries differently, see [[Customizing Plex Libraries]]._


## Local Paths

### Media


| Path                   | Purpose                                                                                                                                                            |
|:---------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <pre>/mnt/local/Media</pre>     | <pre> Location of media stored on the server. Sonarr/Radarr imports will go here.   </pre>                                                                                                                         |
| <pre>/mnt/plexdrive/Media</pre> | <pre> Location of media stored on Google Drive (mounted by Plexdrive) </pre>                                                                                                  |
| <pre>/mnt/unionfs/Media</pre>   | <pre> Combined folder of local media (/mnt/local/Media) and online media (/mnt/plexdrive/Media). <br /><br /> This is the folder that Plex, Sonarr, and Radarr read when scanning for media.</pre> |

Note: Make sure `/mnt/local` has enough space to store the imported media.

### UnionFS Cleaner


| Path               | Purpose                                                                                                                                                                                       |
|:------------------ |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <pre>/mnt/local/Media</pre> | <pre> Location of media stored on the server. <br /><br /> Size of this path is checked periodically (default 30 min). When the folder size reaches its threshold (default 200GB), media will be moved to Google Drive, freeing up local disk space </pre> |

Note: For more info, see the [[UnionFS Cleaner]] page.


## Docker Paths

The Dockerized app (e.g. Plex) will "see" the **Docker Path**, but that path will actually be the **Host Path** on the server. 

By default, NZBGet and ruTorrent downloads are stored in `~/downloads` on the server (i.e **Host Path**), however, this can be changed to point elsewhere (e.g. a second hard drive) by editing the [[settings.yml|Configuring-Settings]] file. But regardless of the download location chosen, the **Docker Path** will always be the same.

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
| <pre>/logs     </pre>     | <pre>/opt/plex/Library/Application Support/Plex Media Server/Logs</pre> | <pre> Location of Plex logs </pre> |
