
##  1. User account setup  ### 

Choose **ONE** of the following:

###    i. Create a new user account `seed` (recommended)

In this step, you will create the user account `seed` and add it to the `seed` and `sudo` groups.  


Run the following commands line by line:


```bash
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

_Note: If you have an existing user account that you don't plan on using, it may be a good idea to remove it and just stick with using `seed` for everything._

###    ii. Create a new user account other than `seed`

Run the following commands line by line:

```bash
sudo useradd -m <username>
sudo usermod -aG sudo <groupname>
sudo passwd <username>
su <username>
```

Set `user` in [[settings.yml|First Time Install: Configuring Settings]] to your username and replace all mentions of `seed:seed` in the wiki with your `username:groupname`.

_Note: If you decide to change your username after Cloudbox install, you will need to update the service.d files with your new username/group, see [[FAQ|FAQ#error-process-xxxxx-execstopbinfusermount--uz-mntplexdrive-codeexited-status217user]]._


###    iii. Use an existing user account

Set `user` in [[settings.yml|First Time Install: Configuring Settings]] to your username and replace all mentions of `seed:seed` in the wiki with your `username:groupname`.

_Note: If you decide to change your username after Cloudbox install, you will need to update the service.d files with your new username/group, see [[FAQ|FAQ#error-process-xxxxx-execstopbinfusermount--uz-mntplexdrive-codeexited-status217user]]._





## 2. Install Dependencies  ####

Run the following command:

```bash
sudo apt-get update && sudo apt-get install -y git python-pip python3-pip python-setuptools python3-setuptools && sudo easy_install -U pip && sudo easy_install3 -U pip && sudo python -m pip install ansible==2.3.1.0 requests && sudo python3 -m pip install requests
```

_Note: Cloudbox uses Ansible v2.3.1.0 because it is the current stable version (v2.3.2.0 has a [[bug|https://github.com/ansible/ansible/issues/27960]] where `docker_container state=stopped` causes the container to be removed)._


## 3. Download Cloudbox ### 



 ```bash
git clone http://github.com/cloudbox/cloudbox ~/cloudbox && cd ~/cloudbox
 ```

_Note: If you use the URL shown on the GitHub page, which is capitalized, and do not specify the path to clone to, the folder created will be capitalized as well (i.e. `Cloudbox`). To fix this, simply rename it to lowercase `cloudbox` via `mv ~/Cloudbox ~/cloudbox`._