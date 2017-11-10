Note: The Ubuntu kernel needs to be updated to 4.10-generic (or higher) before Cloudbox can be installed. If your kernel is already up to date, you may skip this step.

1. Go into the Cloudbox folder

    ```bash
    cd ~/cloudbox
    ```

3. Run the following command:

    ```bash
    sudo ansible-playbook cloudbox.yml --tags kernel
    ```

4. Once the kernel update is done, the server will reboot automatically. If it doesn't, run the following command: 

    ```bash
    sudo reboot
     ```