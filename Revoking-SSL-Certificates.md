In case you wanted to revoke the SSL certificates for some reason (e.g. switch to another domain name), here are the commands to do so. Run these as user (not sudo).

Note: This is not required if you are simply migrating Cloudbox to another server via [[backup and restore | Backup and Restore]] and intend to use the same domain name (update the [[DNS settings|Prerequisites#3-domain-name]] for your domain name, if required).

1. Revoking keys for the domain:

   ```bash
   /opt/scripts/nginx/revoke_certs.sh
   ```

1. Before re-running Cloudbox with your new settings (e.g. domain name changes), it is advised to remove all the docker containers before hand. <sup name="a1">[\[1\]](#f1) </sup><sup name="a2">[\[2\]](#f2)</sup>


   ```bash
   docker stop $(docker ps -aq)
   docker rm $(docker ps -aq)
   ```



***

<sup><b name="f1">[1](#a1)</b> Cloudbox install will try to remove all the docker containers before installing, but it's better to remove them manually, beforehand. </sup>

<sup><b name="f2">[2](#a2)</b> If you need to keep other non-Cloudbox containers, you may just remove the nginx-proxy container, instead, before re-running Cloudbox. </sup>