## 1. Editing Settings ##

  ```bash
    nano ~/cloudbox/settings.yml
  ```

## 2. Overview of Settings ## 

```yaml
---
user: seed
passwd: password123
domain: testcloudbox.ml
email: your@email.com
cloudflare_api_token:
nzbget:
  downloads: /mnt/local/downloads/nzbget
rutorrent:
  passwd: password321
  downloads: /mnt/local/downloads/rutorrent
plex:
  tag: public
  transcodes: /home/{{user}}/transcodes
plex_autoscan:
  ip: 0.0.0.0
rclone:
  version: latest
unionfs_cleaner:
  max_local_gigabytes: 200
  size_check_mins: 30
  rclone_remote: 'google:'
backup:
  tar_dest: /home/{{user}}/Backups
  rsync_dest: rsync://somehost.com/Backups
  rclone_dest: google:/Backups
  keep_local_copy: true
  use_rsync: false
  use_rclone: false
  cron_time: weekly
  cron_state: absent
  pushover_app_token:
  pushover_user_key:
```

## 3. Options in Settings

To see the information below in a nice-looking table, click [[here|https://pste.eu/p/4Ycx.html]]. (not working right now)


---


- `user`: User account for Cloudbox. If user account with this name does not already exist, it will be created for you. Default is `seed`. This parameter is required.

- `passwd`: Password for new account. You can leave it as empty quotes (`""`) if an account was already created. 

  - Note: Password **must** be in alphanumeric characters. No special characters. 

- `domain`: Your domain name. To be used to access your Cloudbox server. If you don't have one, see [[Prerequisites| Basics: Prerequisites#3-domain-name]].

- `email`: Your e-mail address.

  - This email will be used to register the Let's Encrypt SSL certifications. You will get certification expiration notices to this e-mail address. 

  - This email is also used for Cloudflare authentication (i.e. use this email in your Cloudflare account).

- `cloudflare_api_token`: By filling this out, you will allow Cloudbox to register the subdomains to Cloudflare DNS (CDN/proxy off), on your behalf, automatically. By leaving it blank, all Cloudflare related functions will be ignored. 

- `nzbget`

    - `downloads`: Path for NZBGet downloads. Default is `/mnt/local/downloads/nzbget`. 

- `rutorrent`:

    - `passwd`: Password to be used for ruTorrent webgui

      - Note: Password **must** be in alpha or alphanumeric characters (but not only numeric ones). No special characters. 

    - `downloads`: Path for ruTorrent downloads. Default is `/mnt/local/downloads/rutorrent`. 

- `plex`:

  - `tag`: Options are `public` or `plexpass`. Default is `public`.

    - Note: Use `plexpass` only if you have an active [Plex Pass](https://www.plex.tv/features/plex-pass/). If you decide to change this later, you will need to update Plex by running the Cloudbox install command with the "update-plex" tag (i.e. `sudo ansible-playbook cloudbox.yml --tags update-plex`).

  - `transcodes`: Path of temporary transcoding files. Default is `"/home/{{user}}/transcodes"`. 

    - Note: **DO NOT** use /tmp or /dev/shm as a transcode location. On reboots, /tmp and /dev/shm are cleared and this causes docker to recreate the folder as root, causing the plex transcoder to crash. See this comment from a Plex employee: [https://forums.plex.tv/discussion/comment/1502936/#Comment_1502936](https://forums.plex.tv/discussion/comment/1502936/#Comment_1502936).

- `rclone`:

  - `version`: Rclone version. Default listed version is the most currently, stable version. Default is `1.38`.

- `unionfs_cleaner`:

  - `max_local_gigabytes`: Max size in GB allowed for local media before is moved to the cloud. Default is `200`. 

  - `size_check_mins`: How often in minutes local media size is checked. Default is `30`.

  - `rclone_remote`: Remote path for Google Drive (see [[Prerequisites| Basics: Prerequisites#4-google-drive-account]]). Default is `"google:"`.

- `backup`:

  - `tar_dest`: Path for local backups (.tar). Only the two of the most recent copies are kept. Default is `"/home/{{user}}/Backups"`.

    - Note: Ensure the path does NOT have a trailing slash ( / ) or else backup will fail (i.e. `/sample/path`, not `/sample/path/`).

  - `rsync_dest`: Path for rsync backups (.tar). Only the two of the most recent copies are kept.

    - Note: Ensure the path does NOT have a trailing slash ( / ) or else backup will fail (i.e. `/sample/path`, not `/sample/path/`).

  - `rclone_dest`: Path for cloud (i.e Google Drive) backups. Only the two most recent copies are kept. Default is `google:/Backups`.

    - Note: Ensure the path does NOT have a trailing slash ( / ) or else backup "could" fail (i.e. `/sample/path`, not `/sample/path/`).

  - `keep_local_copy`: Option to save local copies of the backup file in `tar_dest` after backup is complete. Default is `true`. 

  - `use_rsync`: Option to enable/disable rsync backups. Options are `true` or `false`. Default is `false`.

  - `use_rclone`: Option to enable/disable cloud (i.e Google Drive) backups. Options are `true` or `false`. Default is `false`.

  - `cron_time`: How often to backup should run (only when `cron_state` is set to `present`). Options are `reboot`, `yearly`, `annually`, `weekly`, `daily`, or `hourly`. Default is `weekly`. 

    - Note: It is not recommended to schedule backups hourly as backing up may take a long time and cause future backup attempts to fail (the backup will not occur while another one is in progress, thanks to backup.lock file being created/removed during this process). 

  - `cron_state`: Option to enable/disable automatic backups. Options are `absent` or `present`. Default is `absent`.

    - `absent` will remove any existing backup schedule. 

    - `present` will ensure it is always scheduled.

    - Note 1: Whenever this option is changed (i.e. "`absent` -> `present`" or "`present` -> `absent`"), a manual backup (`sudo ansible-playbook cloudbox.yml --tags backup`) must be run once in order to enable or disable the backup schedule.  

    - Note 2: This option just allows Cloudbox to schedule the backup for you. You can manually schedule cron (e.g. `sudo crontab -e`) to run backups with `/usr/local/bin/ansible-playbook /home/seed/cloudbox/cloudbox.yml --tags backup` called as root. 

  - `pushover_app_token`: Pushover App Token. Enables notifications to be sent when a backup task starts and finishes (requires both the `Pushover App Token` and the `Pushover User Key`). Default is blank.

  - `pushover_user_key`: Pushover User Key. Enables notifications to be sent when a backup task starts and finishes (requires both the `Pushover App Token` and the `Pushover User Key`). Default is blank.


## 3. Saving Settings ## 

- `Ctrl-x`, `y`, and `enter` to save.

