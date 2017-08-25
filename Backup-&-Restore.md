"Before restoring your backup, ensure that the existing plex server is offline, otherwise it will cause issues when the new system tries to identify itself to plex as the old system, yet the old system is still up and connected to plex"

# Backup

# Restore

1. Enable either rsync or rclone under backup of settings.yml

2. If using rclone, drop in your rclone.conf into ~/cloudbox...

Easy way:

nano rclone
paste

3. Run command

sudo ansible-playbook cloudbox.yml --tag restore

4. Install Cloudbox