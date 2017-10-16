## 1. Editing Settings ##

  ```bash
    cd ~/cloudbox
    nano settings.yml
  ```

## 2. Overview of Settings ## 

```yaml
---
  user: seed
  passwd: password123
  domain: testcloudbox.ml
  email: your@email.com
  nzbget:
    downloads: "/home/{{user}}/downloads/nzbget"
  rutorrent:
    passwd: password321
    downloads: "/home/{{user}}/downloads/rutorrent"
  plex:
    tag: public
    transcodes: "/home/{{user}}/transcodes"
  plex_autoscan:
    ip: "0.0.0.0"
  rclone:
    version: 1.36
  unionfs_cleaner:
    max_local_gigabytes: 200
    size_check_mins: 30
    rclone_remote: "google:"
  backup:
    tgz_dest: "/home/{{user}}/Backups"
    rsync_dest: rsync://somehost.com/Backups
    rclone_dest: google:/Backups
    use_rsync: false
    use_rclone: false
    cron_time: weekly
    cron_state: absent
```

## 3. Options in Settings

To see the information below in a nice table, click [[here|https://pste.eu/p/G1fe.html]].


---


- `user`: User account for Cloudbox (will be created if it doesn't exist already). Default is `seed`. This variable is required.

- `passwd`: Password for user account (only needed if user account is being created). Leave blank if not needed.

  - Note: Password **must** be in alphanumeric characters. No special characters. 

- `domain`: Your domain name. To be used to access your Cloudbox server. If you don't have one, see [[Prerequisites|Prerequisites#3-domain-name]].

- `email`: Your e-mail address. This is used to get SSL certificates.

  - Note: This requires a valid e-mail address or else the certificates will fail.
- `nzbget`

    - `downloads`: Path for NZBGet downloads. Default is `"/home/{{user}}/downloads/nzbget"`. 

- `rutorrent`:

    - `passwd`: Password to be used for ruTorrent webgui

      - Note: Password **must** be in alpha or alphanumeric characters (but not only numeric ones). No special characters. 

    - `downloads`: Path for ruTorrent downloads. Default is `"/home/{{user}}/downloads/rutorrent"`. 

- `plex`:

  - `tag`: Options are `public` or `plexpass`. Default is `public`.

    - Note: Use `plexpass` only if you have an active [Plex Pass](https://www.plex.tv/features/plex-pass/). This can be changed later by running the installer again.

  - `transcodes`: Path of temporary transcoding files. Default is `"/home/{{user}}/transcodes"`. 

    - Note: **DO NOT** use /tmp or /dev/shm as a transcode location. On reboots, /tmp and /dev/shm are cleared and this causes docker to recreate the folder as root, causing the plex transcoder to crash. See this comment from a Plex employee: [https://forums.plex.tv/discussion/comment/1502936/#Comment_1502936](https://forums.plex.tv/discussion/comment/1502936/#Comment_1502936).

- `plex_autoscan`

  - `ip`: Server IP that Plex_Autoscan will listen on. Default is `0.0.0.0`. 

    - Note: Should not be changed because containers can not communicate with host via 127.0.0.1.

- `rclone`:

  - `version`: Rclone version. Should not be changed as this is the most stable tested version. Default is `1.36`.

- `unionfs_cleaner`:

  - `max_local_gigabytes`: Max size in GB allowed for local media before is moved to the cloud. Default is `200`. 

  - `size_check_mins`: How often in minutes local media size is checked. Default is `30`.

  - `rclone_remote`: Should not be changed. Default is `"google:"`.

- `backup`:

  - `tgz_dest`: Path for local backups (.tar). Only the two of the most recent copies are kept. Default is `"/home/{{user}}/Backups"`.

    - Note: Ensure the path does NOT have a trailing slash (/) or else backup will fail (i.e. `/sample/path`, not `/sample/path/`).

  - `rsync_dest`: Path for rsync backups (.tar). Only the two of the most recent copies are kept.

    - Note: Ensure the path does NOT have a trailing slash (/) or else backup will fail (i.e. `/sample/path`, not `/sample/path/`).

  - `rclone_dest`: Path for cloud (i.e Google Drive) backups. Only the two most recent copies are kept. Default is `google:/Backups`.

    - Note: Ensure the path does NOT have a trailing slash (/) or else backup "could" fail (i.e. `/sample/path`, not `/sample/path/`).

  - `use_rsync`: Option to enable/disable rsync backups. Options are `true` or `false`. Default is `false`.

  - `use_rclone`: Option to enable/disable cloud (i.e Google Drive) backups. Options are `true` or `false`. Default is `false`.

  - `cron_time`: How often to backup should run (only when `cron_state` is set to `present`). Options are `reboot`, `yearly`, `annually`, `weekly`, `daily`, or `hourly`. Default is `weekly`. 

    - Note 1: It is not recommended to schedule backups hourly as backing up may take a long time and cause future backup attempts to fail (the backup will not occur while another one is in progress, thanks to backup.lock file being created/removed during this process). 

    - Note 2: This option just allows the script to schedule the backup for you. You can manually schedule cron to run backups with `ansible-playbook cloudbox.yml --tags backup` called as root.

  - `cron_state`: Option to enable/disable automatic backups. Options are `absent` or `present`. Default is `absent`.

    - `absent` will remove any existing backup schedule. 

    - `present` will ensure it is always scheduled.

    - Note: When this option changed (whether to `present` or `absent`), a manual backup must be run once in order to set the backup schedule (i.e. `sudo ansible-playbook cloudbox.yml --tags backup`). In case the `absent` option is set, it will disable further backups after running the manual backup; however, you can manually remove the cron job (i.e. `sudo crontab -e`) if you did not want to run a manual backup command to do so.

## 3. Saving Settings ## 

- `Ctrl-X`, then `Y`, then `enter` key.

