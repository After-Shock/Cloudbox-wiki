Updating Cloudbox is not required, but steps below are provided if you want to do so. 


Steps are typically:

1. Ensure you have a recent [[backup | Backup and Restore#backup]]. 


2. Pull the latest changes:

   ```bash
   cd ~/cloudbox
   git pull
   ```

3. If it says `settings.yml` has been modified, make a backup of that file, delete it, and git pull again. You will need to edit the [[settings.yml| Configuring Settings]] file and replace the default variables with your custom ones (do not just replace/overwrite the settings.yml file with your backed up one, as this error typically indicates the default settings.yml has been modified, e.g. new variables have been added).

4. You can now run the Cloudbox installer with your preferred tag (see [[this|Installing-Cloudbox]]). Your existing data (e.g. Plex, Sonarr, Radarr, etc) will remain intact.

   ```bash
   sudo ansible-playbook cloudbox.yml --tags full
   ```

5. Reboot {_you should always perform a reboot after installing Cloudbox_).

   ```bash
   sudo reboot
   ```


