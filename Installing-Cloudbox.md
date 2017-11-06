
1. Go into the Cloudbox folder

    ```bash
    cd ~/cloudbox
    ```

2. Decide on what type of Cloudbox you want: `full`,`feeder`, or `plex`. For most cases, this will usually be `full`. 

3. Run the following command, with the preferred option from #2 (`--tags "option"`). Quotes are not required.
     
   ```bash
   sudo ansible-playbook cloudbox.yml --tags full
   ```

   This will start the Cloudbox install.

4. When asked for a Plex Claim Token (_not the same as a Plex login token - a Plex Claim Token starts with `CLAIM_`_), go to https://plex.tv/claim, login to your Plex account if required, copy the claim token, and paste it at the prompt. When you paste it, you will see nothing; this is normal. Just press enter to continue.

    ![Plex Claim Token Prompt](http://i.imgur.com/SkRnay2.png)

    ![Plex Claim Token](https://i.imgur.com/HZJ2Oqo.png)

5. The next screen will show you what claim token was submitted (it will be shown in lowercase) and will continue with the rest of the Cloudbox install.

    ![Plex Claim Token Shown](http://i.imgur.com/ubnNg3I.png)

    - Note: If you make a mistake in pasting the claim token, you may either:
 
      - Use SSH Tunneling to log into Plex and set your credentials
        - Create tunnel via ngrok: `ngrok http 32400`
        - Go to the http page ngrok generates (format of http://XXXXXXXX.ngrok.io)
        - Set your credentials in Plex. 
      - Abort the install and run install again
        - To abort: `Ctrl + c`, then `a`  
        - Remove Plex Container: `sudo docker rm -f plex` (it may show "Error response from daemon: No such container" if not created yet)
        - Remove the Plex folder: `sudo rm -rf /opt/plex`. 
        - Redo installation (step #3). 


6. You must now reboot.
    ```bash
    sudo reboot
     ```
