If you want to keep your Cloudbox up-to-date with new additions/changes etc, then follow the guide below. 

_Note 1: You will not lose your config files (e.g. Plex/Sonarr/Radarr libraries, etc) as that is stored in `/opt`, but it is still prudent to have a recent [[backup | Backup and Restore#backup]], anyway._ 

_Note 2: You will not lose any custom/extra Docker containers you have installed (though they may be stopped and require starting manually), since running/updating Cloudbox only updates Cloudbox related apps and docker containers._

Steps to update Cloudbox are below.


1. Pull the latest changes (your `settings.yml` file will remain intact).

   ```bash
   cd ~/cloudbox && git pull
   ```

1. If you get any errors during `git pull`, you will need to reset the Cloudbox git folder (i.e. `~/cloudbox/`). 

   If you are on the `develop` branch:
   ```bash
   git reset --hard origin/master
   ```

   If you are on the `develop` branch:
   ```bash
   git reset --hard origin/develop
   ```

1. Run the Cloudbox installer with your preferred [[tag|First Time Install: Installing-Cloudbox]]. 

   Note: Your existing data (i.e. UnionFS Cleaner, Plex Autoscan, App configs, etc) will remain intact and you will not be asked for a Plex Claim Token if you've already setup Plex.

   ```bash
   sudo ansible-playbook cloudbox.yml --tags full
   ```
   
1. If new variables (e.g. new features) are to be added to your `settings.yml file`, you will get a message before Cloudbox (prematurely) exists:

   ```
   TASK [settings : Check 'settings-updater.py' run status for new settings] **********************************************************************************************************************************************************
   Tuesday 01 May 2018  14:54:42 +0200 (0:00:00.019)       0:00:03.900 ***********
   fatal: [localhost]: FAILED! => {"changed": false, "failed": true, "msg": "The script 'settings_updater.py' added new settings. Check `settings-updater.log` for details of new setting names added."}
          to retry, use: --limit @/home/seed/cloudbox/cloudbox.retry

   PLAY RECAP *************************************************************************************************************************************************************************************************************************
   localhost                  : ok=8    changed=1    unreachable=0    failed=1
   ```

1. Take a look at your `settings.yml` file and/or the `settings_updater.log` log file to see what was added. 

1. After making any necessary changes to your `settings.yml` file, re-run the Cloudbox installer.

1. Reboot when the install completes.

   ```bash
   sudo reboot
   ```