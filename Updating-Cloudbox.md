Updating cloudbox is not recommended, but it can be done. Steps are typically:

1. Ensure you have a recent [[backup | Backup & Restore#backup]]. 


2. Pull the latest changes:

   ```bash
   cd ~/cloudbox
   git pull
   ```

3. If it says `settings.yml` has been modified, make a backup of that file, delete it, and git pull again. You will need to edit the [[settings.yml| Configuring Settings]] file and replace the default variables with your custom ones (do not just replace the settings.yml file with your backed up one, as this error typically indicates the default settings.yml has been modified, e.g. new variables have been added).

4. You can now run Cloudbox installer. We advise you to use the `-e 'no_kernel=true'` to avoid updating the kernel again. Your existing data (e.g. Plex, Sonarr, Radarr, etc) will remain intact.

   ```bash
   sudo ansible-playbook cloudbox.yml --tags full -e 'no_kernel=true'
   ```

5. Reboot {_you should always perform a reboot after installing Cloudbox_).

   ```bash
   sudo reboot
   ```


