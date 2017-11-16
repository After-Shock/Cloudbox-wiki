Before Cloudbox can be installed, the Ubuntu kernel needs to be updated to 4.10-generic (or higher). 

_Note 1: If your kernel is already updated, you may skip this step._

_Note 2: If you are using a Scaleway server, read [[this|FAQ#if-you-are-using-a-scaleway-server]]._


1. Go into the Cloudbox folder:

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