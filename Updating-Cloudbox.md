Updating Cloudbox is not required, but steps below are provided if you want to do so. 


Steps are typically:

1. Ensure you have a recent [[backup | Backup and Restore#backup]]. 


2. Pull the latest changes:

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

      Make a backup of that file (`cp settings.yml ~/`), delete it (`rm settings.yml`), and git pull again. You will need to edit the [[settings.yml| Configuring Settings]] file and replace the default variables with your custom ones. 

      Do not just replace/overwrite the settings.yml file with your backed up one, as this error typically indicates the default settings.yml has been modified (e.g. new variables have been added).

    - If it says a lot of files has been modified, like... 

      ```
      error: Your local changes to the following files would be overwritten by merge:
          .github/cloudbox-animated.gif
          README.md
          cloudbox.yml
          docs/CHANGELOG.md
          docs/cb_logo_1.gif
          roles/backup/tasks/main.yml
          roles/common/tasks/main.yml
          roles/jackett/tasks/main.yml
          roles/motd/files/10-sysinfo
          roles/motd/files/20-package-updates
          roles/motd/files/30-security-updates
          roles/motd/tasks/main.yml
          roles/nginx-proxy/files/proxy.conf
          roles/nzbget/tasks/main.yml
          roles/nzbhydra/tasks/main.yml
          roles/plex/tasks/main.yml
          roles/plex_autoscan/templates/config.json.js2
          roles/radarr/tasks/main.yml
          roles/restore/tasks/main.yml
          roles/rutorrent/tasks/main.yml
          roles/scripts/tasks/main.yml
          roles/sonarr/tasks/main.yml
          settings.yml
      Please, commit your changes or stash them before you can merge.
      ```

      Make a backup of that file (`cp settings.yml ~/`). Reset the clone (`git reset --hard origin/master`), and git pull again. Take a look at your settings.yml file and compare with the new one. If there are any changes (e.g. new variables added), you will need to edit the [[settings.yml| Configuring Settings]] and bring your previous info over. 

4. You can now run the Cloudbox installer with your preferred [[tag|Installing-Cloudbox]]. Your existing data will remain intact and you will not be asked for a Plex Claim Token if you've already setup Plex.

   ```bash
   sudo ansible-playbook cloudbox.yml --tags full
   ```

5. Reboot {_you should always perform a reboot after installing Cloudbox_).

   ```bash
   sudo reboot
   ```


