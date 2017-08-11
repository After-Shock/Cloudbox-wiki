**Note: Run each command line one by one.**

###  1. Create user account for Cloudbox and set the password for it ### 
```bash
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

Note: The user can be changed, but it will also require updating the user variable inside [[settings.yml|Configuring Settings]].


### 2. Clone Cloudbox project ### 

```bash
sudo apt-get install git
cd ~
git clone http://github.com/l3uddz/cloudbox
cd cloudbox
git checkout develop
```