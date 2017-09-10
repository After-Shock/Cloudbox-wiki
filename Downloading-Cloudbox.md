**Note: Run each command line by line. Don't just paste it all at once.**

###  1. Create user account `seed` for Cloudbox and set the password for it ### 
```bash
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

Note: The user name `seed` can be changed to something else, but it will also require updating the user variable inside [[settings.yml|Configuring Settings]] (and other places) and replacing any mentions of `seed` with your username in future commands.


### 2. Clone Cloudbox project ### 

```bash
sudo apt-get update && sudo apt-get install -y git
cd ~
git clone http://github.com/l3uddz/cloudbox
cd cloudbox
git checkout develop
```