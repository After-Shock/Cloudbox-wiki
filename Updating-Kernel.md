Note: The Ubuntu kernel needs to be updated before Cloudbox can run. If your kernel version is 4.10-generic or higher, you may skip this page.

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