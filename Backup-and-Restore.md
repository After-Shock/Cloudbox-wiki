Backup is an integral part of Cloudbox, this is what makes it so great! Everything related to installed applications is backed up. Any changes made to service files in /etc/systemd/system is also backed up. However, Seeding content is NOT backed up.


Cloudbox Backup will backup
- `/opt` folder - all app databases and settings. This includes Plex, Sonarr, Radarr, NZBGet, Rutorrent/rTorrent, NZBHydra, Jackett, Portainer, Organizr, Nginx (including SSL Keys), Plex Autoscan, and Unionfs Cleaner.
- service files in `/etc/systemd/system`
- settings.yml file from `~/cloudbox/settings.yml`
- Rclone config file from `~/cloudbox/settings.yml`

# Backup


Everything else is backed up. Any configuration changes made inside /opt/ e.g. plex_autoscan and unionfs_cleaner are backed up and will be used for future restores. 
The end result is you will have a .tar file that will be uploaded to your google drive storage/rsync remote. This backup file can then be restored on a brand new server, with everything exactly as you left it at the time of backup. 

Backup can be done on a schedule via the cron options (remember that you must run the backup once in order for it to apply the cron schedule changes in settings.yml) - you can also manually create a cron schedule, but it MUST be ran as the root user (e.g. sudo crontab -e). to create a manual cron you should use the following command todo the backup ```ansible-playbook /home/USER/cloudbox/cloudbox.yml --tags backup``` - remmber this MUST be ran as root so it does not have any unforseen permission issues.

In order todo a manual backup, you can ```cd ~/cloudbox``` ```sudo ansible-playbook cloudbox.yml --tags backup```.

Please remember, if you want your seeding content to be also backed up, you will have to handle that yourselves as that is something we have no intention of supporting. If you would like todo that, you can tar your downloads folder, and upload it seperately. 

Only /opt is backed up, so dont expect your /home folder and other stuff to be backed up, as it will not be, and could cause data loss if you were expecting it to be.


```
a manual backup must ALWAYS be ran
for anything in settings.yml to take effect
so even if its enabled when u first install it
backup role is never ran
to set that stuff
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