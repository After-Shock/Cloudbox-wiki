<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:0 -->

- [Intro](#intro)
- [Backup](#backup)
	- [Manual Backup](#manual-backup)
	- [Scheduled Backup](#scheduled-backup)
- [Restore](#restore)


<!-- /TOC -->

---



# Intro

Backup and Restore is an integral part of Cloudbox, this is what makes it so great! Everything related to installed applications is backed-up. Seeding content, however, is NOT backed-up.

**Cloudbox Backup** creates a backup .tar file of the entire `/opt` folder, which includes all settings and configuration files for the Docker apps installed with Cloudbox, and uploads it to your Google Drive or Rsync remote. Backup can be ran manually on-demand or scheduled to run automatically.

**Cloudbox Restore** downloads the backup .tar file and and restores it to the `/opt` folder. This can be done on the same server or brand new one, with everything exactly as you left it at the time of backup. 

_Note 1: If you are restoring to a new server with a different IP address, you will need to update the [[DNS settings|Prerequisites#3-domain-name]] for your domain name._

_Note 2: If you are restoring to a new server and would like to use a different domain name, it is a good idea to revoke the SSL certificates for the current domain name before backing up. This will free up your domain name from Let’s Encrypt's certificates and you will be able to use it in the future without having to wait for the previous certificates to expire (~90 days). More info at [[Revoking SSL Certificates]]_.

<br />


| Things That Are Backed-up | Backed-up From            | Restored To              |
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

1. Go into your Cloudbox folder 
 
   ```shell
   cd ~/cloudbox 
   ```

2. Run the backup command

   ```shell
   sudo ansible-playbook cloudbox.yml --tags backup
   ```

## Scheduled Backup

There are 2 ways to schedule a Cloudbox Backup: (1) Have Cloudbox setup the schedule for you , or (2) creating a cron job, manually.

### Have Cloudbox Setup a Backup Schedule

1. Set the following in your [[settings.yml|Configuring Settings]] file:

   - `tar_dest` (default location is OK)

   - `use_rsync` and/or `use_rclone` to `true` (based on your preference).

     - Note: If both options are set to `true`, backups will be made to both locations, but only Rclone will be used to retrieve the backup file during restore (i.e. Rclone will take priority over Rsync during restores).

   - `rsync_dest` and/or `rclone_dest` (based on your preference).

   - `cron_time` (schedule to of your preference)

   - `cron_state` to `present`

   - `pushover_app_token` and `pushover_user_key` if you wish to receive [[Pushover]] notifications during backup tasks.


   Note: See the [[Configuring Settings]] wiki page for further details on all the settings listed above. 


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


### Setup a Backup Schedule in Cron

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

1. [[Download Cloudbox|Downloading Cloudbox]] (all steps within).

1. [[Update the kernel|Updating-Kernel]].

1. Set the following in your [[settings.yml|Configuring Settings]] file (the bare minimum for a restore):

   - `user` (based on the user account you created in step #1)

   - `tar_dest` (default location is OK)

   - `use_rsync` and/or `use_rclone` to `true` (based what you used during backup)

     - Note: If both options are set to `true`, only Rclone will be used to retrieve the backup file (i.e. Rclone will take priority over Rsync).

   - `rsync_dest` and/or `rclone_dest` (based what you used during backup)

   Note: See the [[Configuring Settings]] wiki page for further details on all the settings listed above. 

1. If your using Rclone, upload your rclone.conf file into `~/cloudbox/`. You may also `nano ~/cloudbox/rclone.conf` and paste the contents of your rclone.conf. 

1. Run the restore command (in `~/cloudbox`).

   ```bash
   sudo ansible-playbook cloudbox.yml --tag restore
   ```

1. Configure the rest of your [[settings.yml|Configuring Settings]]. 

   Note: You may use your previous settings.yml file (`/opt/settings.yml`) as a point of reference to update your new one. However, if all the variables are the same (i.e. no new or modified variables), you may just replace it with your previous one (`cp /opt/settings.yml ~/cloudbox/`).


1. [[Install Cloudbox|Installing Cloudbox]].

After install, everything will be as it was at the time of backup.