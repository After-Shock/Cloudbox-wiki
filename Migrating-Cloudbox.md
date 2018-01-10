This guide will outline some basic steps to copy/move your Cloudbox setup to another server and/or another domain name. 

Listed below are some scenarios and steps to follow for them. 


### Copy Cloudbox to Another Server and Change the Domain Name

1. Create a [backup](Backup-and-Restore#manual-backup) of your Cloudbox server. 

1. [Restore](Backup-and-Restore#restore) Cloudbox to the new server (skip step #7). 

1. Register your new domain name (if you haven't already) and point the DNS to your new server. 

1. Edit the [[settings.yml|Configuring Settings]] file, and type in your new domain name. 

1. Remove the old SSL certificate files: 
   
   ```
   rm -rf /opt/nginx-proxy
   ```
1. Run the Cloudbox [[Installer|Installing Cloudbox]].