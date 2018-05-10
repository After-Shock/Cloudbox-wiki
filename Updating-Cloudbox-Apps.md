The info below will show you how to update your Cloudbox apps (to update your entire Cloudbox, see [[Updating Cloudbox]]).


## Update to a newer version

To simply update to a newer version, see table below. 

_Note: We prefer `docker stop/start <container>` vs `docker restart <container>`, to prevent corrupting data, especially on apps like ruTorrent._

| Cloudbox Apps                                      | How to update                                                                                                                      |
|:-------------------------------------------------- |:---------------------------------------------------------------------------------------------------------------------------------- |
| Plex                                               | Auto updates on container restart: `docker stop plex && docker start plex`                                                         |
| PlexPy                                             | Update within the app                                                                                                              |
| Plex AutoScan                                      | Update git project: `cd /opt/plex_autoscan && git pull` <br /> Restart service: `sudo systemctl restart plex_autoscan.service`     |
| Sonarr                                             | Auto updates on container restart: `docker stop sonarr && docker start sonarr`                                                     |
| Radarr                                             | Auto updates on container restart: `docker stop radarr && docker start radarr`                                                     |
| NZBGet                                             | Auto updates on container restart: `docker stop nzbget && docker start nzbget`                                                     |
| ruTorrent                                          | Update the docker container (see next table)                                                                                       |
| Jackett                                            | Auto updates on container restart: `docker stop jackett && docker start jackett`                                                   |
| NZB Hydra                                          | Auto updates on container restart: `docker stop nzbhydra && docker start nzbhydra`                                                 |
| Plex Requests - Meteor                             | Update within the app                                                                                                              |
| Organizr                                           | Update within the app                                                                                                              |
| Portainer                                          | Update the docker container (see next table)                                                                                       | 
| UnionFS Cleaner<sup name="a1">[\[1\]](#f1) </sup> | Update git project: `cd /opt/unionfs_cleaner && git pull` <br /> Restart service: `sudo systemctl restart unionfs_cleaner.service` |

<br />

<sup><b name="f1">[1](#a1)</b></sup> To turn on auto-update:  edit `/opt/unionfs_cleaner/config.json` and set `"use_git_autoupdater"` to `true`. 


<br />


## Rebuild the Docker containers

Alternatively, you can rebuild the docker container, outright.  This is particularly useful if you have made certain modifications to the Ansible role and need it to run without having to reinstall Cloudbox. 

Run the following commands in `~/cloudbox/`.


| Cloudbox Docker-based Apps  | How to rebuild (`sudo ansible-playbook cloudbox.yml --tags `)                                                 |
|:--------------------------- |:--------------------------------------------------------------- |
| Plex                        | `update-plex`         |
| PlexPy                      | `update-plexpy`       |
| Sonarr                      | `update-sonarr`       |
| Radarr                      | `update-radarr`       |
| NZBGet                      | `update-nzbget`       |
| ruTorrent                   | `update-rutorrent`    | 
| Jackett                     | `update-jackett`      |
| NZB Hydra                   | `update-nzbhydra`     |
| Plex Requests - Meteor      | `update-plexrequests` |
| Organizr                    | `update-organizr`     |
| Portainer                   | `update-portainer`    |
| Watchtower                  | `update-watchtower`   |
| Nginx-Proxy and Letsencrypt | `update-nginx`        |

