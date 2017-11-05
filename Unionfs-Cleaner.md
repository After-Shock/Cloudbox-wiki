### What is UnionFS Cleaner?

UnionFS Cleaner moves all your content in `/mnt/local/Media/` (see [[Paths|Paths#unionfs_cleaner]]) to Google Drive after the folder reaches a certain threshold. This was first set during initial install of Cloudbox via the [[settings.yml|Configuring Settings]] file, but can also be changed after (see below). 

You media is being upgraded by Sonarr or Radarr, it will delete the previous files. When that data is still on the local server, it is immediately deleted, but when it has been moved to Google Drive, it UnionFS will instead create a whiteout file (blank _HIDDEN~ file) that will make the old file invisible to Sonarr, Radarr, and Plex, but the media will still exist on Google Drive. UnionFS Cleaner will scan for these whiteout files, and remove the corresponding files from Google Drive, keeping your content free of duplicates. 


Perform scan of .unionfs folder for _HIDDEN~ files, if file exists on remote, delete it and the _HIDDEN~ file. Perform automated rclone moves on your local media when X gigabytes has been reached and no files are currently being accessed. Perform automated rsync backups on specified folders after X hours.


A few things to mention on UnionFS Cleaner. 

* Unionfs_Cleaner comes pre set for the default paths used by Cloudbox (see [[Paths]]).

  If you are using sub-dirs within the default paths (e.g. Media/Movies/Kids etc) then this will also be caught / uploaded.

the default configuration can be found at /opt/unionfs_cleaner/config.json - if you wish to receive notifications, edit that file and put in your pushover app token and pushover user token, save it and then it will restart itself, so dont worry about restarting it. notifications will be sent when uploads begin / skipped due to files being accessed / upload cancelled due to ban/interval restored after a ban sleep of 25hrs has completed).

the default local content max size / check interval can be edited whenever via changing them in that configuration file and saving it causing unionfs_cleaner to reload itself.

if you want to know more about each configuration setting, read the readme @ github.com/l3uddz/unionfs_cleaner