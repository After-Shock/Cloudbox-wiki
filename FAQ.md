- ### Can I install this on an ARM machine?

  ARM is not supported.

- ### Unrar module fails to install during the Common Role step?


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

- ### Get pip ssl errors?

   - Run `sudo easy_install pyOpenSSL` and retry.

- ### Error connecting: Error while fetching server API version: Timeout value connect was Timeout(connect=60, read=60, total=None), but it must be an int or float.

  - Run `sudo pip install requests==2.10.0` and retry.
