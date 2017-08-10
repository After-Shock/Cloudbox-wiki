## 1. Run these commands ##

```
cd ~/cloudbox
nano settings.yml
```

## 2. Change settings ## 

 - Overview:

    ![](http://i.imgur.com/qGnqJ1n.png)

- `user`: User account for Cloudbox (will be created if it doesn't exist already). Default is `seed`.
- `passwd`: Password for user account if user account is being created. 
- `domain`: Domain name for reverse proxy.
- `email`: D-mail used for SSL cert files.
- `nzbget`
    - `downloads`: Path for NZBGet downloads. Default is `"/home/{{user}}/downloads/nzbget"`. 
- `rutorrent`:
    - `passwd`: Password to be used for ruTorrent webgui
    - `downloads`: Path for ruTorrent downloads. Default is `"/home/{{user}}/downloads/rutorrent"`. 
- `plex`:
  - `tag`: Options are `public` or `plexpass`. Use `plexpass` only if you have an active [Plex Pass](https://www.plex.tv/features/plex-pass/). This can be changed later by running the installer again. Default is `public`.
  - `transcodes`: Path of temporary transcoding files. Default is `"/home/{{user}}/transcodes"`. 
    - Note: DO NOT use /tmp or /dev/shm as a transcode location. On reboots, /tmp and /dev/shm is cleared and this causes docker to recreate the folder as root, causing the plex transcoder to crash. 
- `plex_autoscan ip`: Server IP that Plex_Autoscan will listen on. Default is `0.0.0.0`. Note: Should not be changed because containers can not communicate with host via 127.0.0.1.
- `rclone`:
  - `version`: Rclone version. Should not be changed as `1.36` has been tested stable.
- `unionfs_cleaner`:
  - `max_local_gigabytes`: Max size in GB allowed for local media before is moved to the cloud. Default is `200`. 
  - `size_check_mins`: How often in minutes local media size is checked. Default is `30`.
  - `rclone_remote`: Should not be changed.
- `backup`:
  - `tgz_dest`: Path for local backups (.tgz). Only the two most recent copies are kept. Default is `"/home/{{user}}/Backups"`.
    - Note: Ensure the path does NOT have a trailing slash (/) or else backup will fail (i.e. `/sample/path`, not `/sample/path/`).
  - `rsync_dest`: Path for rsync backups (.tgz). Only the two most recent copies are kept.
    - Note: Ensure the path does NOT have a trailing slash (/) or else backup will fail (i.e. `/sample/path`, not `/sample/path/`).
  - `rclone_dest`: Path for cloud backups. Only the two most recent copies are kept. Default is `google:/Backups`.
    - Note: Ensure the path does NOT have a trailing slash (/) or else backup "could" fail (i.e. `/sample/path`, not `/sample/path/`).
  - `use_rsync`: Option to enable/disable rsync backup. Options are `true` or `false`. Default is `false`.
  - `use_rclone`: Option to enable/disable cloud backup. Options are `true` or `false`. Default is `false`.
  - `stop_plex`: Option to shutdown Plex before backup. Default is `false`. 
    - Note: It is highly recommended to set this as `true`, since this will cause Plex to be stopped while /opt is archived, and brought backup immediately upon archive creation, just before upload. This will prevent potential corruption of the Plex SQLite database. However, this option MUST BE `false` for feeder installations; otherwise, the backup will fail.
  - `cron_time`: How often to backup should run (only when `cron_state` is set to `present`). Options are `reboot`, `yearly`, `annually`, `weekly`, `daily`, or `hourly`. Default is `weekly`. 
    - Note 1: It is not recommended to schedule backups hourly as backing up may take a long time and cause future backup attempts to fail (the backup will not occur while another one is in progress, thanks to backup.lock file being created/removed during this process). 
    - Note 2: This option just allows the script to schedule the backup for you. You can manually schedule cron to run backups with `ansible-playbook cloudbox.yml --tags backup` called as root.
  - `cron_state`: Option to enable or disable automatic backups. Options are `absent` or `present`. Default is `absent`.
    - `absent` will remove any existing backup schedule. 
    - `present` will ensure it is always scheduled.
    - Note: When this option changed (whether to `present` or `absent`), a manual backup must be run once in order to set the backup schedule (i.e. `sudo ansible-playbook cloudbox.yml --tags backup`). In case the `absent` option is set, it will disable further backups after running the manual backup; however, you can manually remove the cron job (i.e. `sudo crontab -e`) if you did not want to run a manual backup command to do so.

## 3. Save settings ## 

- `CTRL-X`, then `y`, then `enter` key.

