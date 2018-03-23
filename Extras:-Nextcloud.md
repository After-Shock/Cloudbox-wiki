Nextcloud is a free, open-source, self-hosted file sharing solution, that functions similarly to Dropbox. 

## 1. Accessing Nextcloud

 - To access Nextcloud, visit https://nextcloud._yourdomain.com_

## 2. First Time Setup

### 1. Add a Subdomain for Nextcloud

 - See [[Adding a Subdomain | Extras: Adding a Subdomain]] on how to add the subdomain `nextcloud` to your DNS provider.

### 2. Set a Password for MariaDB

1. Run the following command: 

   ```
   nano ~/cloudbox/roles/nextcloud/tasks/main.yml
   ```
1. Set `MYSQL_ROOT_PASSWORD:` to a password of your choosing.

   Example:
   ```yaml
   MYSQL_ROOT_PASSWORD: "password321"
   ```
1. `Ctrl-x`, `y`, and `enter` to save.

### 3. Install Nextcloud and MariaDB

Run the following commands: 

 ```bash
 cd ~/cloudbox/
 sudo ansible-playbook cloudbox.yml --tags install-nextcloud  
 ```

### 4. Setup Wizard

1. Visit https://nextcloud._yourdomain.com_

   ![](https://i.imgur.com/akcVDEl.png)

1. Under `Create an admin account`, set the following:

   - Username: fill in your preferred admin username. 

   - Password: fill in your preferred admin password. 

1. Click the `Storage & database` link. 

   ![](https://i.imgur.com/BRpV7i6.png)

1. Under `data folder`, the path below should already be filled in. 
  
   ```
   /data
   ```


3. Select `MySQL/MariaDB` under `Configure the database`.

   ![](https://i.imgur.com/Ck012rr.png)

4. Fill in the following: 

   - Database user: `root`

   - Database password: your [[MYSQL_ROOT_PASSWORD | Extras: Nextcloud#2-set-a-password-for-mariadb]]. 

   - Database name: `nextcloud`

   - Database host: `mariadb:3306`

5. Click `Finish setup`. 
   				
   ![](https://i.imgur.com/jU8wOUD.png)

6. You will now be logged into Nextcloud.

### 5. Add Folder(s)

1. Click the icon at the top right and select "Apps". 

   ![](https://i.imgur.com/cHQUv1Z.png)

1. Enable `External storage support`. Type in your admin password to confirm. 

   ![](https://i.imgur.com/2nKCBVt.png)

1. Click the icon at the top right and select "Settings". 

   ![](https://i.imgur.com/c3vDcR7.png)

1. Click "External storages" under "Administration".

   ![](https://i.imgur.com/Gi7Lhxe.png)

1. For each folder you want to add, set the following: 

   1. Folder name: folder name. 

   1. External storage: `local`. 

   1. Authentication: your preference (default is `None`). 

   1. Configuration: `/mnt/unionfs/Media/path/to/folder` (make sure this path already exists; you could even share your entire `/mnt/unionfs/Media/` path). 

   1. Available for: your preference (default is blank - for all users).

   1. Press the checkmark to save. 

   ![](https://i.imgur.com/YCLJm5w.png)