Before Cloudbox can be installed, the Ubuntu kernel needs to be updated to 4.10-generic or higher. 

- You can use Cloudbox to update the kernel (see below) or you could do this manually via `sudo apt install linux-generic-hwe-16.04` + `sudo reboot`.

- See the following links if you using the following servers: [[Scaleway|FAQ#if-you-are-using-a-scaleway-server]], [[OVH|FAQ#if-you-are-using-an-ovh-server]].

- If your kernel is already updated, you may skip this page.

Steps to update the kernel via Cloudbox:

1. Go into the Cloudbox folder:

    ```bash
    cd ~/cloudbox
    ```

3. Run the following command:

    ```bash
    sudo ansible-playbook cloudbox.yml --tags kernel
    ```
   This may take a while to complete.

4. Once the kernel update is done, the server will reboot automatically. If it doesn't, run the following command:

    ```bash
    sudo reboot
     ```
