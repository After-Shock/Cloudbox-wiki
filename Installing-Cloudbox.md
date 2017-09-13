## 1. Downloading Cloudbox ## 

_Note: Run each command one by one._ 


 ```bash
 cd ~
 git clone http://github.com/l3uddz/cloudbox
 cd cloudbox
 git checkout master
 ```

## 2. Running Cloudbox  ### 


1. Go into the cloudbox folder (if not already there)

    ```bash
    cd ~/cloudbox
    ```

2. Decide on what type of Cloudbox you want: `full`,`feeder`, or `plex` .

3. Run the following command, with the preferred option from #2 (`--tag "option"`). Quotes are not required.

    Example of a full install:
      ```bash
      sudo ansible-playbook cloudbox.yml --tag full
      ```
4. When asked for a Plex Claim Token (_not the same as a Plex login token - a Plex Claim Token starts with `CLAIM_`_), go to https://plex.tv/claim, login to your Plex account if required, copy the claim token, and paste it at the prompt. When you paste it, you will see nothing; this is normal. Just press enter to continue.

    ![Plex Claim Token Prompt](http://i.imgur.com/SkRnay2.png)

    ![Plex Claim Token](https://i.imgur.com/HZJ2Oqo.png)

5. The next screen will show you what claim token was submitted (it will be shown in lowercase).

    ![Plex Claim Token Shown](http://i.imgur.com/ubnNg3I.png)

    Note: If you make a mistake in pasting the claim token, you may abort the install by pressing `Ctrl + C`, then `A`. You must then stop and remove the Plex container via `sudo docker rm -f plex` (it may show an error if it hasn't been created yet) and remove the Plex folder via `sudo rm -rf /opt/plex`. Then run the installation again (step #3).

6. You must now reboot.
    ```bash
    sudo reboot
     ```
