--WORK IN PROGRESS--

## What is UnionFS Cleaner?

UnionFS Cleaner moves all your content in `/mnt/local/Media/` (see [[Paths|Paths#unionfs_cleaner]]) to Google Drive after the folder reaches a certain threshold. This was first set during initial install of Cloudbox via the [[settings.yml|Configuring Settings]] file, but can also be changed after (see below). 

When Sonarr or Radarr upgrade your media files, they delete the previous ones. When that data is still on the local server, it is deleted, immediately, but when it has been moved to Google Drive, it is unable to do so because it is mounted as read-only (via Plexdrive). Instead, UnionFS creates a whiteout file (a blank `filename.ext_HIDDEN~` file) that makes the file invisible. But the media will still exist on Google Drive. To resolve this, UnionFS Cleaner will scan for a whiteout file, remove the corresponding file from Google Drive, remove it's _HIDDEN~ file, and as a result, keep your content free of duplicates. 


## UnionFS Cleaner Config




### Enable Pushover Notifications

Notifications will be sent when:
- an upload task begins
- an upload task is skipped due to files being accessed
- an upload is cancelled due to ban (i.e. `error 403`) and UnionFS Cleaner is put into a 25 hour sleep.
- when UnionFS Cleaner is the restored after the ban sleep


To enable Pushover notifications, see [[this|Pushover#unionfs-cleaner]].


### Modify Upload Threshold


* To Moedify 

Perform scan of .unionfs folder for _HIDDEN~ files, if file exists on remote, delete it and the _HIDDEN~ file. Perform automated rclone moves on your local media when X gigabytes has been reached and no files are currently being accessed. Perform automated rsync backups on specified folders after X hours.


A few things to mention on UnionFS Cleaner. 



the default configuration can be found at /opt/unionfs_cleaner/config.json - if you wish to receive notifications, edit that file and put in your pushover app token and pushover user token, save it and then it will restart itself, so dont worry about restarting it. 

the default local content max size / check interval can be edited whenever via changing them in that configuration file and saving it causing unionfs_cleaner to reload itself.

if you want to know more about each configuration setting, read the readme @ github.com/l3uddz/unionfs_cleaner