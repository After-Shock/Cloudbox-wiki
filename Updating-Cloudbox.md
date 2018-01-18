Updating Cloudbox is not required, but if you may do so to keep your Cloudbox up to date.

_Note 1: You will not lose your config files (e.g. Plex/Sonarr/Radarr libraries, etc) as that is stored in `/opt`, but it is still prudent to have a recent [[backup | Backup and Restore#backup]], anyway._ 

_Note 2: You will not lose any custom/extra Docker containers you have installed (though they may be stopped and require starting manually), since running/updating Cloudbox only updates Cloudbox related apps and docker containers._

Steps to update cloudbox are below:

1. Pull the latest changes:

   ```bash
   cd ~/cloudbox
   git pull
   ```

   - If it says `settings.yml` has been modified, like... 


      ```
      error: Your local changes to the following files would be overwritten by merge:
          settings.yml
      Please, commit your changes or stash them before you can merge.
      ```

      You'll need to do the following: 
      
      1. Make a backup of the settings.yml file

          ```
          cp settings.yml ~/
          ```

      2. Delete the old settings.yml file

          ```
          rm settings.yml
          ```

      3. Pull the latest changes

          ```
          git pull
          ```
      

      4. Edit settings.yml 

          You will need to edit this new [[settings.yml| Configuring Settings]] file and replace the default variables with the ones from your saved one (`~/settings.yml`). 

          Note: Do not just replace/overwrite the settings.yml file with your backed up one, as this error typically indicates the default settings.yml has been modified (e.g. new variables have been added).

    - If it says a lot of files have been modified, like... 

      ```
      error: Your local changes to the following files would be overwritten by merge:
          .github/cloudbox-animated.gif
          README.md
          cloudbox.yml
          docs/CHANGELOG.md
          roles/radarr/tasks/main.yml
          roles/restore/tasks/main.yml
          roles/rutorrent/tasks/main.yml
          roles/scripts/tasks/main.yml
          roles/sonarr/tasks/main.yml
          settings.yml
      Please, commit your changes or stash them before you can merge.
      ```

      You'll need to do the following: 
      
      1. Make a backup of the settings.yml file

          ```
          cp settings.yml ~/
          ```

      2. Reset the git folder

          ```
          git reset --hard origin/master
          ```

      3. Pull the latest changes

          ```
          git pull
          ```
  
      4. Edit settings.yml 

          Compare your previous settings.yml file with the new one. If there are any changes (e.g. new variables added), you will need to edit the [[settings.yml| Configuring Settings]] and bring your previous info over. 

          Note: Resetting the git clone will not reset your config files (e.g. `/opt`); it will merely update the Cloudbox installer files located in `~/cloudbox`.

2. You can now run the Cloudbox installer with your preferred [[tag|Installing-Cloudbox]]. Your existing data will remain intact and you will not be asked for a Plex Claim Token if you've already setup Plex.

   ```bash
   sudo ansible-playbook cloudbox.yml --tags full
   ```

3. Reboot {_you should always perform a reboot after installing Cloudbox_).

   ```bash
   sudo reboot
   ```


