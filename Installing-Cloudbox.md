## 1. Install Ansible ###

Run the following commands (one by one). Press `Y` when asked to confirm.
```bash
sudo apt-get install -y python-pip
sudo pip install ansible==2.3.1.0
```
Note: Ansible v2.3.1.0 is the current stable version (v2.3.2.0 has a bug where docker_container state=stopped causes container to be removed).


## 2. Install Cloudbox

1. Go into cloudbox folder

    ```bash
    cd ~/cloudbox
    ```

2. Decide on what type of Cloudbox you want: `full`,`feeder`, or `plex` .

3. Run the following command, with the preferred option from #2 (`--tag "option"`). Quotes are not required.

    Example of a full install:
      ```bash
      sudo ansible-playbook cloudbox.yml --tag full
      ```
4. When asked for a Plex Claim Token, go to https://plex.tv/claim, copy the claim token, and paste it at the prompt. When you paste it, you will see nothing; this is normal. Just press enter to continue.

    ![Plex Claim Token](http://i.imgur.com/SkRnay2.png)

5. The next screen will show you what claim token was submitted (it will be shown in lowercase).

    ![Plex Claim Token Shown](http://i.imgur.com/ubnNg3I.png)

    Note: If you make a mistake and submit an incorrect claim token, you may abort the install by pressing `Ctrl + C`, then `A`. You must then stop and remove the Plex container via `sudo docker rm -f plex` (it may show an error if it hasn't been created yet) and remove the Plex folder via `sudo rm -rf /opt/plex`. Then run the installation again (step #3).

5. You must now reboot.
    ```bash
    sudo reboot
     ```
