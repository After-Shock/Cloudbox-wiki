Note: Kernel needs to be updated, to a minimum of 4.10 generic, before Cloudbox install is run.

1. Go into the cloudbox folder (if not already there)

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