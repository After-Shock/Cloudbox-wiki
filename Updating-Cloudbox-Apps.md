The info below will show you how to update your Cloudbox apps (to update the your entire Cloudbox, see [[Updating Cloudbox]].)


## Update to a newer version:

To simply update to a newer version, see table below.

| Cloudbox Apps                                     | How to update                                                                                                                       |
|:------------------------------------------------- |:----------------------------------------------------------------------------------------------------------------------------------- |
| Plex                                              | Auto updates on container restart: `docker restart plex`                                                                            |
| PlexPy                                            | Update within the app.                                                                                                              |
| Plex AutoScan                                     | Update git project: `cd /opt/plex_autoscan && git pull` <br /> Restart serviced: `sudo systemctl restart plex_autoscan.service`     |
| Sonarr                                            | Auto updates on container restart: `docker restart sonarr`                                                                          |
| Radarr                                            | Auto updates on container restart: `docker restart radarr`                                                                          |
| NZBGet                                            | Auto updates on container restart: `docker restart nzbget`                                                                          |
| ruTorrent                                         | Update the docker container (see other table)                                                                                       |
| Jackett                                           | Auto updates on container restart: `docker restart jackett`                                                                         |
| NZB Hydra                                         | Auto updates on container restart: `docker restart nzbhydra`                                                                        |
| Plex Requests - Meteor                            | Update within the app.                                                                                                              | 
| Organizr                                          | Update within the app.                                                                                                              |
| Portainer                                         | Update the docker container (see other table)                                                                                       |
| UnionFS Cleaner <sup name="a1">[\[1\]](#f1) </sup> | Update git project: `cd /opt/unionfs_cleaner && git pull` <br /> Restart serviced: `sudo systemctl restart unionfs_cleaner.service` |

<br />

<sup><b name="f1">[1](#a1)</b></sup> To turn on auto-update:  edit `/opt/unionfs_cleaner/config.json` and set `"use_git_autoupdater"` to `true`. 


<br />


## Rebuild the Docker containers

Alternatively, you can rebuild the docker container, outright.  This is particularly useful if you have made certain modifications to the Ansible role and need it to run without having to reinstall Cloudbox. 

Run the following commands in `~/cloudbox/`.


| Cloudbox Docker-based Apps  | How to rebuild                                                  |
|:--------------------------- |:--------------------------------------------------------------- |
| Plex                        | `sudo ansible-playbook cloudbox.yml --tags update-plex`         |
| PlexPy                      | `sudo ansible-playbook cloudbox.yml --tags update-plexpy`       |
| Sonarr                      | `sudo ansible-playbook cloudbox.yml --tags update-sonarr`       |
| Radarr                      | `sudo ansible-playbook cloudbox.yml --tags update-radarr`       |
| NZBGet                      | `sudo ansible-playbook cloudbox.yml --tags update-nzbget`       | 
| ruTorrent                    | `sudo ansible-playbook cloudbox.yml --tags update-rutorrent`   |
| Jackett                     | `sudo ansible-playbook cloudbox.yml --tags update-jackett`      |
| NZB Hydra                   | `sudo ansible-playbook cloudbox.yml --tags update-nzbhydra`     |
| Plex Requests - Meteor      | `sudo ansible-playbook cloudbox.yml --tags update-plexrequests` |
| Organizr                    | `sudo ansible-playbook cloudbox.yml --tags update-organizr`     |
| Portainer                   | `sudo ansible-playbook cloudbox.yml --tags update-portainer`    |
| Watchtower                  | `sudo ansible-playbook cloudbox.yml --tags update-watchtower`   |
| Nginx-Proxy and Letsencrypt | `sudo ansible-playbook cloudbox.yml --tags update-nginx`        |




***
