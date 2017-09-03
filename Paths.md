## Local Paths

### Media


| Path                   | Purpose                                                                                                                                                            |
|:---------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `/mnt/local/Media`     | Sonarr/Radarr imports will go here                                                                                                                                 |
| `/mnt/plexdrive/Media` | Media that is stored on Google Drive is mounted here (Plexdrive)                                                                                                   |
| `/mnt/unionfs/Media`   | Combined folder of local media (`/mnt/local/Media`) and online media (`/mnt/plexdrive/Media`). This is the folder Plex, Sonarr, Radarr will read during disk scans |


### UnionFS_Cleaner


| Path               | Purpose                                                                                                                                                                                       |
|:------------------ |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/mnt/local/Media` | Size of the local media folder is checked periodically. When the folder size reaches it's threshold (default `250GB`), it will move that content to Google Drive, freeing up local disk space |



---

## Docker Paths:

### Plex

| Docker Path    | Host Path                   | Purpose                      |
|:-------------- |:--------------------------- |:---------------------------- |
| `/data/Movies` | `/mnt/unionfs/Media/Movies` | Plex reads this for Movies   |
| `/data/TV`     | `/mnt/unionfs/Media/TV`     | Plex reads this for TV Shows |


### Sonarr


| Docker Path            | Host Path                         | Purpose                                                                 |
|:---------------------- |:--------------------------------- |:----------------------------------------------------------------------- |
| `/tv`                  | `/mnt/unionfs/Media/TV`           | Sonarr will import to `/tv` which in turn is that folder on host system |
| `/downloads/rutorrent` | `~/downloads/rutorrent` (default) | ruTorrent download folder as set in settings.yml                        |
| `/downloads/nzbget`    | `~/downloads/nzbget` (default)    | NZBGet download folder as set in settings.yml                           |


### Radarr


| Docker Path            | Host Path                         | Purpose                                                                     |
|:---------------------- |:--------------------------------- |:--------------------------------------------------------------------------- |
| `/movies`              | `/mnt/unionfs/Media/Movies`       | Radarr will import to `/movies` which in turn is that folder on host system |
| `/downloads/rutorrent` | `~/downloads/rutorrent` (default) | ruTorrent download folder as set in settings.yml                            |
| `/downloads/nzbget`    | `~/downloads/nzbget` (default)    | NZBGet download folder as set in settings.yml                               |


### PlexPy


| Docker Path | Host Path                                                      | Purpose                               |
|:----------- |:-------------------------------------------------------------- |:------------------------------------- |
| `/logs`     | `/opt/plex/Library/Application Support/Plex Media Server/Logs` | Location of Plex logs; used by PlexPy | 
