<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:0 -->

- [Intro](#intro)
- [Backup](#backup)
	- [Manual Backup](#manual-backup)
	- [Scheduled Backup](#scheduled-backup)
- [Restore](#restore)


<!-- /TOC -->

---



# Intro

Backup and Restore is an integral part of Cloudbox, this is what makes it so great! Everything related to installed applications is backed up. 

_Note: Torrent Seeding content, anything in `/mnt/`, `/home/`, or anywhere else other than the `/opt/` folder, will **NOT** be backed up (media files are moved to Google Drive via [[UnionFS Cleaner]], anyway)._

**Cloudbox Backup** creates a backup .tar file of the entire `/opt` folder, which includes all settings and configuration files for the Docker apps installed with Cloudbox, and uploads it to your Google Drive or Rsync remote. Backup can be ran manually for an immediate backup or scheduled to run periodically.

**Cloudbox Restore** downloads the backup .tar file and and restores it to the `/opt` folder. This can be done on the same server or brand new one, with everything exactly as you left it at the time of backup. 

_Note: If you wish to move your Cloudbox to another server, see [[Migrating Cloudbox]]._

<br />


|                           | Backed Up From            | Restored To              |
|:------------------------- |:------------------------- |:------------------------ |
| Plex                      | `/opt/plex/`              | `/opt/plex/`             |
| PlexPy                    | `/opt/plexpy/`            | `/opt/plexpy/`           |
| Plex Requests - Meteor    | `/opt/plexrequests/`      | `/opt/plexrequests/`     |
| Sonarr                    | `/opt/sonarr/`            | `/opt/sonarr/`           |
| Radarr                    | `/opt/radarr/`            | `/opt/radarr/`           |
| NZBGet                    | `/opt/nzbget/`            | `/opt/nzbget/`           |
| Rutorrent/rTorrent        | `/opt/rutorrent/`         | `/opt/rutorrent/`        |
| NZB Hydra                 | `/opt/nzbhydra/`          | `/opt/nzbhydra/`         |
| Jackett                   | `/opt/jackett/`           | `/opt/jackett/`          |
| Portainer                 | `/opt/portainer/`         | `/opt/portainer/`        |
| Organizr                  | `/opt/organizr/`          | `/opt/organizr/`         |
| Nginx config              | `/opt/nginx/`             | `/opt/nginx/`            |
| SSL Certificates          | `/opt/nginx-proxy/`       | `/opt/nginx-proxy/`      |
| Plex Autoscan             | `/opt/plex_autoscan/`     | `/opt/plex_autoscan/`    |
| Unionfs Cleaner           | `/opt/unionfs_cleaner/`   | `/opt/unionfs_cleaner/`  |
| Systemd Service           | `/etc/systemd/system/`    | `/opt/systemd/`          |
| Cloudbox settings         | `~/cloudbox/settings.yml` | `/opt/settings.yml`      |
| Rclone config             | `~/cloudbox/rclone.conf`  | `/opt/rclone/rclone.conf`| 


<br />


Things that are not backed-up:
* home folder (i.e. `~/` or `/home/`)
* ruTorrent downloads folder (i.e. all your seeding content).
* NZBGet downloads folder (i.e. content that has not been moved by Sonarr/Radarr).

<br />

# Backup

## Manual Backup

This is handy for times when you just need to make an immediate backup of your server, regardless of whether you have backup scheduler enabled or not. 

1. Go into your Cloudbox folder 
 
   ```shell
   cd ~/cloudbox 
   ```

2. Set the following in your [[settings.yml|First Time Install: Configuring Settings]] file:

   - `tar_dest` (default: `/home/{{user}}/Backups`)

   - Decide on Rclone or Rsync as your backup method. 

     - If you prefer to use Rclone, set `use_rclone` to `true` and define an `rclone_dest` (default: `google:/Backups`). 

       - _Note: If you have a separate Plex and Feeder setup, you may want to separate your backups into different folders (e.g. `google:/Backups/Plexbox` for your Plexbox and `google:/Backups/Feederbox` for your Feederbox)_

     - If you prefer to use Rsync, set `use_rsync` to `true` and define an `rsync_dest` (default: `rsync://somehost.com/Backups`; you can use the Rsync protocol or a folder path). 

     - Note: If both `use_rclone` and `use_rsync`are set to `true`, backups will be made to both locations, but only Rclone will be used to retrieve the backup file during restore (i.e. Rclone will take priority over Rsync during restores).

   Note: See the [[Configuring Settings | First Time Install: Configuring Settings]] wiki page for further details on all the settings listed above. 


3. Run the backup command

   ```shell
   sudo ansible-playbook cloudbox.yml --tags backup
   ```

## Scheduled Backup

This will schedule Cloudbox backups to run periodically. This is set Cron. 

There are 2 ways to set this up: 

1. [Have Cloudbox setup it up for you](#scheduling-backup-via-cloudbox), or

2. [Create a Cron task, manually](#scheduling-backup-via-cron-manually).

### Scheduling Backup via Cloudbox

1. Set the following in your [[settings.yml|First Time Install: Configuring Settings]] file:

   - `tar_dest` (default: `/home/{{user}}/Backups`)

   - Decide on Rclone or Rsync as your backup method. 

     - If you prefer to use Rclone, set `use_rclone` to `true` and define an `rclone_dest` (default: `google:/Backups`). 

       - _Note: If you have a separate Plex and Feeder setup, you may want to separate your backups into different folders (e.g. `google:/Backups/Plexbox` for your Plexbox and `google:/Backups/Feederbox` for your Feederbox)_

     - If you prefer to use Rsync, set `use_rsync` to `true` and define an `rsync_dest` (default: `rsync://somehost.com/Backups`; you can use the Rsync protocol or a folder path). 

     - Note: If both `use_rclone` and `use_rsync`are set to `true`, backups will be made to both locations, but only Rclone will be used to retrieve the backup file during restore (i.e. Rclone will take priority over Rsync during restores).

   - `cron_time` (schedule to of your preference)

   - `cron_state` to `present`

   - `pushover_app_token` and `pushover_user_key` if you wish to receive [[Pushover]] notifications during backup tasks.


   Note: See the [[Configuring Settings | First Time Install: Configuring Settings]] wiki page for further details on all the settings listed above. 


1. Run a Manual Backup Once

   Note: This step is required even if scheduled backup was enabled (i.e. `cron_state` set to `present`) when you first installed Cloudbox, since a manual backup has to be run once to create the cron job.


   1. Go into your Cloudbox folder.
 
      ```shell
      cd ~/cloudbox 
      ```

   2. Run the backup command.

      ```shell
      sudo ansible-playbook cloudbox.yml --tags backup
      ```


### Scheduling Backup via Cron, Manually

1. Edit the crontab in root.

   ```bash
   sudo crontab -e
   ```

2. Add your cron task. 

   Note: You must use the full Ansible path (i.e. `/usr/local/bin/ansible-playbook /home/seed/cloudbox/cloudbox.yml --tags backup`).

   Example: 

   ```bash
   @weekly /usr/local/bin/ansible-playbook /home/seed/cloudbox/cloudbox.yml --tags backup
   ```


# Restore

We will assume you are restoring to a new / clean server. 

1. [[Download Cloudbox|First Time Install: Downloading Cloudbox]] (all steps within).

1. [[Update the kernel|First Time Install: Updating-Kernel]].

1. Set the following in your [[settings.yml|First Time Install: Configuring Settings]] file (the bare minimum for a restore):

   - `user` (based on the user account you created in step #1)

   - `tar_dest` (default: `/home/{{user}}/Backups`)

   - Decide on Rclone or Rsync as your backup method. 

     - If you prefer to use Rclone, set `use_rclone` to `true` and define an `rclone_dest` (default: `google:/Backups`). 

       - _Note: If you have a separate Plex and Feeder setup, you may want to separate your backups into different folders (e.g. `google:/Backups/Plexbox` for your Plexbox and `google:/Backups/Feederbox` for your Feederbox)_

     - If you prefer to use Rsync, set `use_rsync` to `true` and define an `rsync_dest` (default: `rsync://somehost.com/Backups`; you can use the Rsync protocol or a folder path). 

     - Note: If both `use_rclone` and `use_rsync`are set to `true`, backups will be made to both locations, but only Rclone will be used to retrieve the backup file during restore (i.e. Rclone will take priority over Rsync during restores).

   Note: See the [[Configuring Settings | First Time Install: Configuring Settings]] wiki page for further details on all the settings listed above. 

1. Upload a copy of your rclone.conf file into `~/cloudbox/`. 

   - You can do this via sftp/scp or by running `nano ~/cloudbox/rclone.conf` and pasting the contents of your rclone.conf. 

1. Run the restore command (in `~/cloudbox`).

   ```bash
   sudo ansible-playbook cloudbox.yml --tags restore
   ```

1. Configure the rest of your [[settings.yml|First Time Install: Configuring Settings]]. 

   Note: You may use your previous settings.yml file (`/opt/settings.yml`) as a point of reference to update your new one. However, if all the variables are the same (i.e. no new or modified variables), you may just replace it with your previous one (`cp /opt/settings.yml ~/cloudbox/`).


1. [[Install Cloudbox| First Time Install: Installing Cloudbox]].

After install, everything will be as it was at the time of backup.