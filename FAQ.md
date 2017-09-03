### Can I install this on an ARM machine?

ARM is not natively supported. However, you may be able to get it to work if you have certain errors you can try to fix them individually. See below


#### If Cloudbox install fails at the Common Role for the unrar module:

1. `sudo apt install unrar-free`

2. `sudo nano ~/cloudbox/roles/common/tasks/main.yml` and remove then nano the common role and remove `unrar` from the list.

#### pip ssl errors:

1. `sudo easy_install pyOpenSSL`
