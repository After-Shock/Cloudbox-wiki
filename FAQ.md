### Can I install this on an ARM machine?

ARM is not natively supported. However, you may be able to get it to work if you have certain errors you can try to fix them individually. See below


#### Install fails at Common Role step (due to unrar module):

1. `sudo apt install unrar-free`

2. `sudo nano ~/cloudbox/roles/common/tasks/main.yml` and remove then nano the common role and remove `unrar` from the list.

#### You get pip ssl errors:

1. `sudo easy_install pyOpenSSL`
