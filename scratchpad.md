

plex autoscan:
preconfigured for fresh installations using cloudbox. - caveats are that it is presetup for Movies as Section ID 1 and TV as Section ID 2 (meaning if fresh plex installation you must first add your Movie library then TV library second). 
If the user wishes to have trash emptying then he must manually go to /opt/plex_autoscan/config and edit config.json with his plex token, then sudo systemctl restart plex_autoscan.
Also this will NOT work if the library is empty (which it will be on a default setup) - the user must do a manual scan so that the tv and movie library has atleast 1 item in both sections, otherwise the plex cli scanner doesnt want to run...
User must also add the connection to his sonarr/radarr settings. remember to disable onGrab and onRename (onRename sends no useful info that we can use to scan with).

unionfs_cleaner:
presetup for a fresh cloudbox installation. the user must add their remote to rclone with the name of "google" - if he does not, then he must edit the existing unionfs_cleaner/config.json to the correct values for his setup.
 
 
backup:
it is suggested that plex is NOT running when this is done to prevent the sqlite database from potentially getting corrupted. although this is upto you. 
stop_plex MUST be false when using feeder type (there is no plex). backup will fail otherwise.
cron_time can be the following:
reboot
yearly
annually
monthly
weekly
daily
hourly

You can use hourly, but i would not recommend it as this task could take some time and you dont want lots of failed backups. (the script wont run when another backup is in progress thanks to backup.lock being created/removed during this process)

cron_state can be absent or present only. absent will remove any existing backup schedule. present will ensure it is always scheduled.

important note: cron is only scheduled after the backup tag has been used. if you want to disable the cron too, you must edit the settings.xml (cron_state to absent) then run the backup and it will remove from cron the scheduled task - or ensure it is there whenever a backup is ran.
note: you can manually remove the cron if wanted so you dont have to run the backup, just ensure you set the cron_state to absent aswell otherwise it will be readded next time you manual backup.

very important note, for rsync backups, ensure your rsync_dest and tgz_dest backup settings DO NOT HAVE A TRAILING SLASH OR IT WILL FAIL.
same goes for rclone, although it may be more fault tolerant, but better to leave the trailing / off all backup path settings


restore:

if the system is a fresh system without rclone, in order for this feature to work to work with use_rclone, you MUST place your rclone.conf inside the same folder as cloudbox.yml. cloudbox will then install rclone, import your .conf then restore /opt from the cloudbox.tgz stored on your remote.
restore will only work with one of rclone or rsync. rclone has priority. if both are enabled then only rclone will be used to retrieve the cloudbox.tgz and restore.
the process is simply install ansible, clone cloudbox, place rclone.conf into cloudbox directory with cloudbox.yml. sudo ansible-playbook cloudbox.yml --tags restore then use the --tags full/feeder/plex whichever you wish to be restored

***** NOTE**********:

Backup and restore does NOT backup any cloudbox settings, e.g. settings.yml - the user MUST keep a copy of this for themselves so they can drop it in along with their rclone.conf (if using rclone backup/restore) before running a restore.

If doing a restore, the user MUST create the user before running a restore otherwise their settings.yml will cause an issue (the user doesnt exist, so it cant chown)

sudo useradd -m USER
sudo passwd USER
sudo usermod -aG sudo USER


*********************

jackett:
make sure to disable auto update. watchtower will update the container for us when theres a new image

plex:

disable DLNA and advertising of ip on entwork
disable chapter thumbnail generation
disable trailers


WHOLE PACKAGE:

Dont perform manual updates via the webtools (sonarr/radarr etc...) watchtower will monitor the docker repo's for updates and autoamtically update them.

organizr:

container ip's on the cloudbox network (for use by organizr in the edit homescreen tab) for local installs
watchtower: 172.18.0.5
traefik: 172.18.0.6 : 8080
netdata: 172.18.0.7 : 19999
organizr 172.18.0.8 : 80
nzbget 172.18.0.9 : 6789
rutorrent 172.18.0.10 : 3111
jackett 172.18.0.11 : 9117
nzbhydra 172.18.0.12 : 5075
sonarr 172.18.0.13 : 8989
radarr 172.18.0.14 : 7878
plex 172.18.0.15 : 32400
plexpy 172.18.0.16 8181
plexrequests 172.18.0.17 : 3000
portainer 172.18.0.18 : 9000

organizr must point to /home for plexpy, e.g. http://plexpy:8181/home

organizr custom theme css:
https://pastebin.com/raw/vG2TgSe3