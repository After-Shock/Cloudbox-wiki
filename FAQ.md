#### Can I install this on an ARM machine?

ARM is not supported.

#### Unrar module fails to install during the Common Role step?


1. Edit the Common Task role:

  ```
  nano ~/cloudbox/roles/common/tasks/main.yml
  ```

1. Replace `unrar` with `unrar-free` under the "Install common packages" section:

  ```
  - name: Install common packages
  apt: "name={{item}} state=installed"
  with_items:

  ```

#### Get pip ssl errors?

 - Run this `sudo easy_install pyOpenSSL` and retry.
