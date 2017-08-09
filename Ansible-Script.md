## 1. Run these commands to create "seed" account
```
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

cd ~
git clone http://github.com/l3uddz/cloudbox
cd cloudbox
git checkout develop
nano settings.yml


edit --> 
passwd
domain
ctrx x to save



sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible

shift Y to yes


sudo ansible-playbook cloudbox.yml --tags full



to continue plex installatio...
https://plex.tv/claim

...

sudo reboot
