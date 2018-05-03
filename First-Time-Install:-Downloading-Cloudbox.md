


## 1. Install Dependencies  ####




```bash
curl -s https://cloudbox.rocks/install_dependencies.sh | sudo sh

```

  or

```bash
wget -qO- https://cloudbox.rocks/install_dependencies.sh | sudo sh
```


_Note: to install Ansible version 2.3.1.0 instead of 2.5.0, add `-s 2.3.1.0` to the end._

## 2. Download Cloudbox ### 



 ```bash
git clone http://github.com/cloudbox/cloudbox ~/cloudbox && cd ~/cloudbox
 ```

_Note: If you `git clone` with the URL shown on the GitHub page, the folder created will be capitalized (i.e. `~/Cloudbox/`). To fix this, simply rename it to lowercase `cloudbox` via `mv ~/Cloudbox ~/cloudbox`._