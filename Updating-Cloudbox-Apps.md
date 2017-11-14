The info below will show you how to update your Cloudbox apps (to update the your entire Cloudbox, see [[Updating Cloudbox]].)


## Update to a newer version:

To simply update to a newer version. 

| Cloudbox Apps          | How to update                                                                                                                                                                                                                              |
|:---------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Plex                   | Restart the docker container: `docker stop plex && docker start plex`                                                                                                                                                                      | 
| PlexPy                 | Update within the app.                                                                                                                                                                                                                     |
| Plex AutoScan          | Update: `cd /opt/plex_autoscan && git pull` <br /> Restart: `sudo systemctl restart plex_autoscan.service`                                                                                                                                 |
| Sonarr                 | Restart the docker container: `docker stop sonarr && docker start sonarr`                                                                                                                                                                  |
| Radarr                 | Restart the docker container: `docker stop radarr && docker start radarr`                                                                                                                                                                  |
| NZBGet                 | Restart the docker container: `docker stop nzbget && docker start nzbget`                                                                                                                                                                  |
| rTorrent               | Update the docker container: `cd ~/cloudbox && sudo ansible-playbook cloudbox.yml --tags update-rutorrent`                                                                                                                                 |
| Jackett                | Restart the docker container: `docker stop jackett && docker start jackett`                                                                                                                                                                |
| NZB Hydra              | Restart the docker container: `docker stop nzbhydra && docker start nzbhydra`                                                                                                                                                              |
| Plex Requests - Meteor | Update within the app.                                                                                                                                                                                                                     |
| Organizr               | Update within the app.                                                                                                                                                                                                                     |
| Portainer              | Update the docker container: `cd ~/cloudbox && sudo ansible-playbook cloudbox.yml --tags update-portainer`                                                                                                                                 |
| UnionFS Cleaner        | Update: `cd /opt/unionfs_cleaner && git pull` <br /> Restart: `sudo systemctl restart unionfs_cleaner.service`  <br /> <br />  To turn on auto-update:  edit `/opt/unionfs_cleaner/config.json` and set `"use_git_autoupdater"` to `true`. |



## Rebuilding the docker containers

Alternatively, you may want to just rebuild the docker container outright.  This is particularly useful if you have made certain modifications to the Ansible roles and need to it to have it run without having to reinstall the entire Cloudbox. 

Run the following commands in `~/cloudbox/`.


| Cloudbox Docker-based Apps  | How to rebuild                                                  |
|:--------------------------- |:--------------------------------------------------------------- |
| Plex                        | `sudo ansible-playbook cloudbox.yml --tags update-plex`         |
| PlexPy                      | `sudo ansible-playbook cloudbox.yml --tags update-plexpy`       |
| Sonarr                      | `sudo ansible-playbook cloudbox.yml --tags update-sonarr`       |
| Radarr                      | `sudo ansible-playbook cloudbox.yml --tags update-radarr`       |
| NZBGet                      | `sudo ansible-playbook cloudbox.yml --tags update-nzbget`       | 
| rTorrent                    | `sudo ansible-playbook cloudbox.yml --tags update-rutorrent`    |
| Jackett                     | `sudo ansible-playbook cloudbox.yml --tags update-jackett`      |
| NZB Hydra                   | `sudo ansible-playbook cloudbox.yml --tags update-nzbhydra`     |
| Plex Requests - Meteor      | `sudo ansible-playbook cloudbox.yml --tags update-plexrequests` |
| Organizr                    | `sudo ansible-playbook cloudbox.yml --tags update-organizr`     |
| Portainer                   | `sudo ansible-playbook cloudbox.yml --tags update-portainer`    |
| Watchtower                  | `sudo ansible-playbook cloudbox.yml --tags update-watchtower`   |
| Nginx-Proxy and Letsencrypt | `sudo ansible-playbook cloudbox.yml --tags update-nginx`        |
