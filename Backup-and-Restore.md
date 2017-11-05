Backup is an integral part of Cloudbox, this is what makes it so great! Everything related to installed applications is backed-up. Seeding content, however, is NOT backed up.

**Cloudbox Backup** creates a .tar file of the entire `/opt` folder, which includes all app databases and settings, and uploads it to your Google Drive or Rsync remote. Backup can be ran manually on-demand or scheduled to run automatically.

**Cloudbox Restore** downloads this this backup .tar file and is able to restore it the same server or even a brand new server, with everything exactly as you left it at the time of backup. With the only thing required is updating of the DNS settings for your domain.


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
| Rclone config             | `~/cloudbox/rclone.conf`  | `/opt/rclone/rclone.conf`| 

   


Things that are not backed up:
* `/home/` folder.
* ruTorrent downloads folder (i.e. all your seeding content).
* NZBGet downloads folder (i.e. content that has not been moved by Sonarr/Radarr).



# Backup

## Manual Backup

1. Go into your Cloudbox folder 
 
   ```shell
   cd ~/cloudbox 
   ```

2. Run the backup command

   ```shell
   sudo ansible-playbook cloudbox.yml --tags backup
   ```

## Scheduled Backup

There are 2 ways to schedule a Cloudbox Backup: (1) by editing the settings.yml file and running a the backup command, or (2) creating a cron task manually.

### 1. Using Cloudbox Settings

1. You will need to edit the [[settings.yml|Configuring Settings]] file and specify:

   - `tgz_dest` (default is OK)

   - `use_rsync` or `use_rclone` based on your preference.

   - `rsync_dest` or `rclone_dest` based on your preference.

   - `cron_time` to a schedule of your preference.

   - `cron_state` to `present`

   -  `pushover_app_token` and `pushover_user_key` if you wish to receive Pushover notification alerts during backup tasks.


   Note: See [[Configuring Settings]] wiki page on further details on all of the settings parameters listed above. 


2. Run a Manual Backup Once

Note: this step is required even if backup was enabled (i.e. `cron_state` set to `present`) when you first installed Cloudbox, since a manual backup has to be run once to create the cron job.


   1. Go into your Cloudbox folder 
 
      ```shell
      cd ~/cloudbox 
      ```

   2. Run the backup command

      ```shell
      sudo ansible-playbook cloudbox.yml --tags backup
      ```


### 2. Creating a cron job manually

1. Edit the crontab in root

   ```bash
   sudo crontab -e
   ```

2. Type in the cron task. Note: you must use the full Ansible path (i.e. `/usr/local/bin/ansible-playbook /home/seed/cloudbox/cloudbox.yml --tags backup`).

   ```bash
   @weekly /usr/local/bin/ansible-playbook /home/seed/cloudbox/cloudbox.yml --tags backup
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