###  1. Run these commands to create "seed" account, set the password when asked. ### 
```
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```
Note: The account name can be changed, but will need to be changed in the [Settings.yml]([[Configuring Settings]]) as well.

### 2. Clone Cloudbox project ### 

```
cd ~
git clone http://github.com/l3uddz/cloudbox
cd cloudbox
git checkout develop
```