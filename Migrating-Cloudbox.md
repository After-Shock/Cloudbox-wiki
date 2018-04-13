This guide will outline some basic steps to copy/move your Cloudbox setup to another server and/or another domain name. 

Listed below are some scenarios and steps to follow for them. 


### Move Cloudbox to Another Server and Keep the Same Domain Name

1. Create a [backup](Backup-and-Restore#manual-backup) of your Cloudbox server. 

1. [Restore](Backup-and-Restore#restore) Cloudbox to the new server (skip step #7). 

   - _Note: Next steps are done on the new server._

1. Point the DNS to your new server. 

1. Run the Cloudbox [[Installer| First Time Install: Installing Cloudbox]].

1. Misc Tips:

   - Update Plex Autoscan URL in Sonarr and Radarr (if the Plex Autoscan URL had the IP address in it). 




### Move Cloudbox to Another Server and Change the Domain Name

1. Create a [backup](Backup-and-Restore#manual-backup) of your current Cloudbox server. 

1. [[Revoke|Revoking SSL Certificates]] your domain's SSL certificates.<sup name="a1">[\[1\]](#f1) </sup>

1. [Restore](Backup-and-Restore#restore) Cloudbox to the new server (skip step #7). 

   - _Note: Next steps are done on the new server._

1. Register your new domain name (if you haven't already) and point the DNS to your new server. 

1. Edit the [[settings.yml|First Time Install: Configuring Settings]] file, and type in your new domain name. 

1. Delete the previous SSL certificate files: 
   
   ```
   rm -rf /opt/nginx-proxy
   ```

1. Run the Cloudbox [[Installer| First Time Install: Installing Cloudbox]].

1. Misc Tips:

   - Update Plex Autoscan URL in Sonarr and Radarr (if the Plex Autoscan URL had the IP address in it). 

### Keep Cloudbox on the Same Server but Change the Domain Name

1. Create a [backup](Backup-and-Restore#manual-backup) of your current Cloudbox server (Optional, but recommended). 

1. [[Revoke|Revoking SSL Certificates]] your domain's SSL certificates.<sup name="a1">[\[1\]](#f1) </sup>

1. Register your new domain name (if you haven't already) and point the DNS to your server. 

1. Edit the [[settings.yml|First Time Install: Configuring Settings]] file, and type in your new domain name. 

1. Delete the previous SSL certificate files: 
   
   ```
   rm -rf /opt/nginx-proxy
   ```

1. Run the Cloudbox [[Installer| First Time Install: Installing Cloudbox]].

1. Misc Tips:

   - Update Plex Autoscan URL in Sonarr and Radarr (if the Plex Autoscan URL had the IP address in it). 



---


<sup><b name="f1">[1](#a1)</b> This will free up the domain name from Let’s Encrypt and you will be able to use it in the future without having to wait for the previous certificates to expire (~90 days). </sup>

 