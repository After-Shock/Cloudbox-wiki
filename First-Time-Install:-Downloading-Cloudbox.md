


## 1. Install Dependencies  ####

Run the following command:

```bash
curl -s https://raw.githubusercontent.com/Cloudbox/Cloudbox/develop/roles/scripts/files/install_dependencies.sh | sudo sh

```

or

```bash
wget -qO- -https://raw.githubusercontent.com/Cloudbox/Cloudbox/develop/roles/scripts/files/install_dependencies.sh  | bash
```


## 2. Download Cloudbox ### 



 ```bash
git clone http://github.com/cloudbox/cloudbox ~/cloudbox && cd ~/cloudbox
 ```

_Note: If you use the URL shown on the GitHub page, which is capitalized, and do not specify the path to clone to, the folder created will be capitalized as well (i.e. `Cloudbox`). To fix this, simply rename it to lowercase `cloudbox` via `mv ~/Cloudbox ~/cloudbox`._