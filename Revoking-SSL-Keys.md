In case you wanted to revoke the keys for some reason (eg switch to another domain name), here are the commands to do so. Run these as user (not sudo).

Note: This is not required if you are simply migrating Cloudbox to another server via [[backup and restore | Backup & Restore]] and intend to use the same domain name (update your [[ domain name DNS settings | Prerequisites]], if required).

1. Revoking keys for the domain:

   ```bash
   /opt/scripts/nginx/revoke_certs.sh
   ```

1. Before rerunning Cloudbox with your new settings (e.g. domain name changes), it is advised to remove all the docker containers before hand. <sup id="a1">[1](#f1)</sup><sup id="a2">[2](#f2)</sup>


   ```bash
   docker stop $(docker ps -aq)
   docker rm $(docker ps -aq)
   ```



<sup><b id="f1">1</b> Cloudbox install will try to remove all the docker containers before installing, but it's still better to be safe by removing them manually before hand. [↩](#a1)</sup>
<sup><b id="f2">2</b> If you need to keep other non-cloudbox containers, you may just remove the nginx container, instead, before rerunning Cloudbox. [↩](#a2)</sup>