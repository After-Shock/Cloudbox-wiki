In case you wanted to revoke the SSL certificates/keys for some reason (e.g. using a domain that has been already used for one Cloudbox server on another server), here are the commands to do so. Run these as user (not sudo).

Note: This is not required if you are simply [[Migrating Cloudbox]] to another server via Backup/Restore.  



1. Revoking keys for the domain:

   Run the following script:

   ```bash
   /opt/scripts/nginx/revoke_certs.sh
   ```

   Chose `y` to delete the cert(s)"

   ```
   -------------------------------------------------------------------------------
   Would you like to delete the cert(s) you just revoked?
   -------------------------------------------------------------------------------
   (Y)es (recommended)/(N)o: 
   ```


1. Before re-running Cloudbox with your new settings (e.g. domain name changes), it is advised to remove all the docker containers before hand. <sup name="a1">[\[1\]](#f1) </sup><sup name="a2">[\[2\]](#f2)</sup>


   ```bash
   docker stop $(docker ps -aq)
   docker rm $(docker ps -aq)
   ```



***

<sup><b name="f1">[1](#a1)</b> Cloudbox install will try to remove all the docker containers before installing, but it's better to remove them manually, beforehand. </sup>

<sup><b name="f2">[2](#a2)</b> If you need to keep other non-Cloudbox containers, you may just remove the nginx-proxy container, instead, before re-running Cloudbox. </sup>