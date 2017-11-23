
###  1. Create the user account  ### 

We will create the user account `seed` and add it to the `sudo` group.  

Run the following commands line by line:


```bash
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

_Note 1: You may use another user name other than `seed`. Simply set that as your preferred user name in [[settings.yml|Configuring Settings]] and replace all mentions of `seed` in the wiki with your user name._

_Note 2: If you decide to change your username after Cloudbox install, you will need to update the service.d files with your new username/group, see [[FAQ|FAQ#dont-see-your-google-drive-files-in-mntplexdrive]]_


### 2. Install Prerequisites  ####

Run the following command:

```bash
sudo apt-get update && sudo apt-get install -y git python-pip python3-pip python-setuptools python3-setuptools && sudo easy_install -U pip && sudo easy_install3 -U pip && sudo python -m pip install ansible==2.3.1.0 requests && sudo python3 -m pip install requests
```

_Note: Cloudbox uses Ansible v2.3.1.0 because it is the current stable version (v2.3.2.0 has a [[bug|https://github.com/ansible/ansible/issues/27960]] where `docker_container state=stopped` causes the container to be removed)._


### 3. Download Cloudbox ### 



 ```bash
git clone http://github.com/cloudbox/cloudbox ~/cloudbox && cd ~/cloudbox
 ```

_Note: If you use the URL shown on the GitHub page, which is capitalized, and do not specify the path to clone to, the folder created will be capitalized as well (i.e. `Cloudbox`). Simply, rename it to lowercase `cloudbox` via `mv ~/Cloudbox ~/cloudbox`._