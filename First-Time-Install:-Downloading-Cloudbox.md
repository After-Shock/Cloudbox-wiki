


## 1. Install Dependencies  ####

Run the following command:

```bash
sudo apt-get update && sudo apt-get install -y git python-pip python3-pip python-setuptools python3-setuptools && sudo easy_install -U pip && sudo easy_install3 -U pip && sudo python -m pip install ansible==2.3.1.0 requests && sudo python3 -m pip install requests
```

_Note: Cloudbox uses Ansible v2.3.1.0 because it is the current stable version (v2.3.2.0 has a [[bug|https://github.com/ansible/ansible/issues/27960]] where `docker_container state=stopped` causes the container to be removed)._


## 2. Download Cloudbox ### 



 ```bash
git clone http://github.com/cloudbox/cloudbox ~/cloudbox && cd ~/cloudbox
 ```

_Note: If you use the URL shown on the GitHub page, which is capitalized, and do not specify the path to clone to, the folder created will be capitalized as well (i.e. `Cloudbox`). To fix this, simply rename it to lowercase `cloudbox` via `mv ~/Cloudbox ~/cloudbox`._