--WORK IN PROGRESS--

## What is UnionFS Cleaner?

UnionFS Cleaner moves all your content in `/mnt/local/Media/` (see [[Paths|Paths#unionfs_cleaner]]) to Google Drive after the folder reaches a certain threshold. This was first set during initial install of Cloudbox via the [[settings.yml|Configuring Settings]] file, but can also be changed after (see below). 

When Sonarr or Radarr upgrade your media files, they delete the previous ones. When that data is still on the local server, it is deleted, immediately, but when it has been moved to Google Drive, it is unable to do so because it is mounted as read-only (via Plexdrive). Instead, UnionFS creates a whiteout file (a blank `filename.ext_HIDDEN~` file) that makes the file invisible. But the media will still exist on Google Drive. To resolve this, UnionFS Cleaner will scan for a whiteout file, remove the corresponding file from Google Drive, remove it's _HIDDEN~ file, and as a result, keep your content free of duplicates. 


## UnionFS Cleaner Config

### Overview of the config.json file

```json

{
    "cloud_folder": "/mnt/plexdrive",
    "dry_run": false,
    "du_excludes": ["*.partial~"],
    "local_folder": "/mnt/local/Media",
    "local_folder_check_interval": 30,
    "local_folder_size": 200,
    "local_remote": "google:/Media",
    "lsof_excludes": [
        ".partial~"
    ],
    "pushover_app_token": "",
    "pushover_user_token": "",
    "rclone_bwlimit": "",
    "rclone_checkers": 16,
    "rclone_chunk_size": "8M",
    "rclone_excludes": [
        "**partial~",
        "**_HIDDEN",
        ".unionfs/**",
        ".unionfs-fuse/**"
    ],
    "rclone_remove_empty_on_upload": {
        "/mnt/local/Media/Movies": 1,
        "/mnt/local/Media/TV": 1
    },
    "rclone_transfers": 8,
    "remote_folder": "google:",
    "unionfs_folder": "/mnt/local/.unionfs-fuse",
    "use_config_manager": true,
    "use_git_autoupdater": true,
    "use_upload_manager": true
}
```





### Enable Pushover Notifications

Notifications will be sent when:
- an upload task begins
- an upload task is skipped due to files being accessed
- an upload is cancelled due to ban (i.e. `error 403`) and UnionFS Cleaner is put into a 25 hour ban sleep
- when UnionFS Cleaner is restored after the ban sleep


To enable Pushover notifications, click [[here|Pushover#unionfs-cleaner]].


### Modify Upload Threshold


1. On the server's shell, run the following command:

    ```
    nano /opt/unionfs_cleaner/config.json
    ```

1. Scroll down to the `rclone_remove_empty_on_upload` section.

1. Change `"/mnt/local/Media/Movies": 1` to `"/mnt/local/Media/Movies": 2`. 

   1. This will tell UnionFS Cleaner to not delete the folders immediately under `/mnt/local/Media/Movies` during cleanup.  

   1. Make sure there is a comma (`,`) at the end of all `"path": #` lines - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```json
   "rclone_remove_empty_on_upload": {
       "/mnt/local/Media/Movies": 2,
       "/mnt/local/Media/TV": 1
   },
   ```

1. `Ctrl-x`, `y`, and `enter` to save.

1. UnionFS Cleaner will restart itself when it detects config.json has changed.



* To Moedify 

Perform scan of .unionfs folder for _HIDDEN~ files, if file exists on remote, delete it and the _HIDDEN~ file. Perform automated rclone moves on your local media when X gigabytes has been reached and no files are currently being accessed. Perform automated rsync backups on specified folders after X hours.


A few things to mention on UnionFS Cleaner. 



the default configuration can be found at /opt/unionfs_cleaner/config.json - if you wish to receive notifications, edit that file and put in your pushover app token and pushover user token, save it and then it will restart itself, so dont worry about restarting it. 

the default local content max size / check interval can be edited whenever via changing them in that configuration file and saving it causing unionfs_cleaner to reload itself.

if you want to know more about each configuration setting, read the readme @ github.com/l3uddz/unionfs_cleaner