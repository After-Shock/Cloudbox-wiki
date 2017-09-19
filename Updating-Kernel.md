Note: Kernel needs to be updated to 4.10 generic or above, before Cloudbox can run.

1. Go into the cloudbox folder (if not already there)

    ```bash
    cd ~/cloudbox
    ```

3. Run the following command:

    ```bash
    sudo ansible-playbook cloudbox.yml --tags kernel
    ```

4. The server will automatically reboot once the kernel update is done. If it does not, run the following command: 

    ```bash
    sudo reboot
     ```