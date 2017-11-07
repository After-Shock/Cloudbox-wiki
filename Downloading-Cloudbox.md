
###  1. Creating the `seed` user account  ### 

Run the following commands line by line (don't just paste it all at once):


```bash
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

Note: The user name `seed` can be changed to something else, but it will also require updating the user variable inside [[settings.yml|Configuring Settings]] and replacing any mentions of `seed` with your username in future commands.


### 2. Installing Git, Pip, Easy_install, and Ansible ####

Run the following command:

```bash
sudo apt-get update && sudo apt-get install -y git && sudo apt-get install -y python-pip && sudo easy_install -U pip && sudo pip install ansible==2.3.1.0
```

_Note: Ansible v2.3.1.0 is the current stable version (v2.3.2.0 has a bug where docker_container state=stopped causes container to be removed)._


### 3. Downloading Cloudbox ### 



 ```bash
 cd ~/ && git clone http://github.com/l3uddz/cloudbox
 ```