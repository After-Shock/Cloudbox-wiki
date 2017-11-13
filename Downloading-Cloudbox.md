
###  1. Create the user account  ### 

We will create the user account `seed`. 

Run the following commands line by line (don't just paste it all at once):


```bash
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

_Note: You may use another user name other than `seed`. Simply set that as your preferred user name in [[settings.yml|Configuring Settings]] and replace all mentions of `seed` in the wiki with your user name._


### 2. Install Prerequisites  ####

Run the following command:

```bash
sudo apt-get update && sudo apt-get install -y git python-pip python3-pip python-setuptools python3-setuptools && sudo easy_install -U pip && sudo easy_install3 -U pip && sudo python -m pip install ansible==2.3.1.0 requests && sudo python3 -m pip install requests
```

_Note: Ansible v2.3.1.0 is the current stable version (v2.3.2.0 has a bug where docker_container state=stopped causes container to be removed)._


### 3. Download Cloudbox ### 



 ```bash
 cd ~/ && git clone http://github.com/l3uddz/cloudbox
 ```