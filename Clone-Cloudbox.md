###  1. Run these commands to create "seed" account, set the password when asked. ### 
```
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

### 2. Clone Cloudbox project ### 

```
cd ~
git clone http://github.com/l3uddz/cloudbox
cd cloudbox
git checkout develop
```