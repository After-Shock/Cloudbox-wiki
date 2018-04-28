Before Cloudbox can be installed, the Ubuntu kernel needs to be updated to 4.10-generic or higher. 

If you installed with Ubuntu Server 16.04 LTS with the HWE kernel (see [here](Basics%3A-Prerequisites#2-dedicated-server)), then you can skip this page. 

_Note: You'll need to update the kernel a different way if you are using: [[Scaleway|FAQ#if-you-are-using-a-scaleway-server]] or [[OVH|FAQ#if-you-are-using-an-ovh-server]]._



---

## Update Kernel via Cloudbox

1. Run the following command:

    ```bash
    cd ~/cloudbox
    ```

1. Run the following command:

    ```bash
    sudo ansible-playbook cloudbox.yml --tags kernel
    ```
   _Note: This may take a while to complete._

1. Once the kernel update is done, the server will reboot automatically. If it doesn't, run the following command:

    ```bash
    sudo reboot
     ```

---

## Update Kernel Manually


1. Run the following command:

    ```bash
    sudo apt-get upgrade linux-generic-hwe-16.04
    ```
   
   _Note: This may take a while to complete._

1. Once the kernel update is done, the server will need to be rebooted:

    ```bash
    sudo reboot
     ```
