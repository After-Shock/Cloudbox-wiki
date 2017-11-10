| Cloudbox Apps          | How to update                                                                                  |
|:---------------------- |:---------------------------------------------------------------------------------------------- |
| Plex                   | Restart docker container: `docker stop plex && docker start plex`                              |
| PlexPy                 | Update within the app.                                                                         | 
| Plex AutoScan          | Update git project: `cd /opt/plex_autoscan && git pull`                                        |
| Sonarr                 | Restart docker container: `docker stop sonarr && docker start sonarr`                          |
| Radarr                 | Restart docker container: `docker stop radarr && docker start radarr`                          |
| NZBGet                 | Restart docker container: `docker stop nzbget && docker start nzbget`                          |
| rTorrent               | Update the container: `cd ~/cloudbox && sudo ansible-playbook cloudbox.yml --update-rutorrent` |
| Jackett                | Restart docker container: `docker stop jackett && docker start jackett`                        |
| NZB Hydra              | Restart docker container: `docker stop nzbhydra && docker start nzbhydra`                      |
| Plex Requests - Meteor | Update within the app.                                                                         |
| Organizr               | Update within the app.                                                                         |
| Portainer              | tbd                                                                                            |
| UnionFS Cleaner        | Modify `/opt/unionfs_cleaner/config`: `"use_upload_manager": true`                             |
