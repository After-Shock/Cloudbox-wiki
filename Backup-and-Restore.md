Backup is an integral part of Cloudbox, this is what makes it so great! Everything related to installed applications is backed-up. Seeding content, however, is NOT backed up.

Cloudbox Backup creates a .tar file of the entire `/opt` folder, which includes all app databases and settings, and uploads it to your Google Drive or Rsync remote. Backup can be ran manually on-demand or scheduled to run automatically.

Cloudbox Restore downloads this this backup .tar file and is able to restore it the same server or even a brand new server, with everything exactly as you left it at the time of backup. With the only thing required is updating of the DNS settings for your domain.


| Things that are backed-up | From:                     | To:                      |
|:------------------------- |:------------------------- |:------------------------ |
| Plex                      | `/opt/plex/`              | `/opt/plex/`             |
| Sonarr                    | `/opt/sonarr/`            | `/opt/sonarr/`           |
| Radarr                    | `/opt/radarr/`            | `/opt/radarr/`           |
| NZBGet                    | `/opt/nzbget/`            | `/opt/nzbget/`           |
| Rutorrent/rTorrent        | `/opt/rutorrent/`         | `/opt/rutorrent/`        |
| NZB Hydra                 | `/opt/nzbhydra/`          | `/opt/nzbhydra/`         |
| Jackett                   | `/opt/jackett/`           | `/opt/jackett/`          |
| Portainer                 | `/opt/portainer/`         | `/opt/portainer/`        |
| Organizr                  | `/opt/organizr/`          | `/opt/organizr/`         |
| Nginx config              | `/opt/nginx/`             | `/opt/nginx/`            |
| SSL Keys                  | `/opt/nginx-proxy/`       | `/opt/nginx-proxy/`      |
| Plex Autoscan             | `/opt/plex_autoscan/`     | `/opt/plex_autoscan/`    |
| Unionfs Cleaner           | `/opt/unionfs_cleaner/`   | `/opt/unionfs_cleaner/`  |
| Systemd Service           | `/etc/systemd/system/`    | `/opt/systemd/`          |
| Cloudbox settings         | `~/cloudbox/settings.yml` | `/opt/settings.yml`      |
| Rclone config             | `~/cloudbox/rclone.conf`  | `/opt/rclone/rclon.conf` | 

    


Things that are not backed up:
* `/home/` folder
* Seeding content (i.e. ruTorrent downloads folder)
* NZBGet downloads folder (all downloads should have been moved into `/mnt/local/Media/` by Sonarr/Radarr and then uploaded to Google Drive via UnionFS Cleaner)

# Backup



Backup can be done on a schedule via the cron options (remember that you must run the backup once in order for it to apply the cron schedule changes in settings.yml) - you can also manually create a cron schedule, but it MUST be ran as the root user (e.g. sudo crontab -e). to create a manual cron you should use the following command todo the backup ```ansible-playbook /home/USER/cloudbox/cloudbox.yml --tags backup``` - remmber this MUST be ran as root so it does not have any unforseen permission issues.

In order todo a manual backup, you can ```cd ~/cloudbox``` ```sudo ansible-playbook cloudbox.yml --tags backup```.

Please remember, if you want your seeding content to be also backed up, you will have to handle that yourselves as that is something we have no intention of supporting. If you would like todo that, you can tar your downloads folder, and upload it seperately. 

Only /opt is backed up, so dont expect your /home folder and other stuff to be backed up, as it will not be, and could cause data loss if you were expecting it to be.


```
a manual backup must ALWAYS be ran
for anything in settings.yml to take effect
so even if its enabled when u first install it
backup role is never ran
to set that stuff
```

# Restore

1. Enable either rsync or rclone under backup of settings.yml

2. If using rclone, drop in your rclone.conf into ~/cloudbox...

Easy way:

nano rclone
paste

3. Run command

sudo ansible-playbook cloudbox.yml --tag restore

4. Install Cloudbox

5. Everything will be as it was at the time the backup was created, with the exception of seeding content.