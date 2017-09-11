In case you wanted to revoke the keys for some reason (eg switch to another domain name), here are the commands to do so. Run these as user (not sudo).

1. Stop all containers:

   ```bash
   docker stop $(docker ps -aq)
   ```


1. Revoking keys for the domain:

   ```bash
   /opt/scripts/nginx/revoke_certs.sh
   ```

1. Before rerunning Cloudbox with your new settings (eg domain name change), it is advised to remove all the docker containers before hand. <sup id="a1">[1](#f1)</sup>


   ```bash
   docker rm -f $(docker ps -aq)
   ```



 <b id="f1">1</b> Note: Cloudbox install will try to remove them before installing. But still better to be safe. If you need to keep other non cloudbox containers, you may just remove the nginx container instead before rerunning Cloudbox. [↩](#a1)
