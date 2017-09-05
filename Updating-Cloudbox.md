Updating cloudbox is not recommended, but it can be done. Steps are typically:

Ensure you have a recent backup. git pull to receive the latest changes. If it says settings.yml has been modified, make a backup of that file, delete it, git pull, then replace the old settings.yml variables with your custom variables from your backed up settings.yml (do not just replace it, as this error typically indicates the default settings.yml has been modified, e.g. new variable).

After you are sure you have a backup, and the latest changes from github, your settings.yml updated with your old settings / setting any new settings, run the installer again, which should run through the install again, leaving your existing data (plex/sonarr/radarr etc) in tact.

Always perform a reboot after an install run.