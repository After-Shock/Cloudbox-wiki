###  1. Run these commands to create "seed" user and set the password for it when asked. ### 
```
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

Note: The user can be changed, but it will also require updating the user variable inside [[settings.yml|Configuring Settings]].


### 2. Clone Cloudbox project ### 

```
cd ~
git clone http://github.com/l3uddz/cloudbox
cd cloudbox
git checkout develop
```