## 1. Forward 

We recommend that you **NOT** use root to login and setup Cloudbox. Definitely **DO NOT** mix and match with 2 different accounts (i.e. setup some parts in root and others in a non-root account), doing so will break apps from functioning.<br/>

**_TLDR: Do not use root acount to setup Cloudbox._**

## 2. Setup


Choose **ONE** of the following:

###    i. Create a new user account `seed` (recommended)

In this step, you will create the user account `seed` and add it to the `seed` and `sudo` groups.  


Run the following commands line by line:


```bash
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
sudo chsh -s /bin/bash seed
su seed
```

_Note: If you have an existing user account that you don't plan on using, it may be a good idea to remove it and just stick with using `seed` for everything._

###    ii. Create new user account other than `seed`

Run the following commands line by line:

```bash
sudo useradd -m <username>
sudo usermod -aG sudo <username>
sudo passwd <username>
sudo chsh -s /bin/bash <username>
su <username>
```

Set `user` in [[settings.yml|First Time Install: Configuring Settings]] to your username and replace all mentions of `seed:seed` in the wiki with your `username:groupname`.

_Note: If you decide to change your username after Cloudbox install, you will need to update the service.d files with your new username/group, see [[FAQ|FAQ#error-process-xxxxx-execstopbinfusermount--uz-mntplexdrive-codeexited-status217user]]._


###    iii. Use an existing (non-root) user account

```bash
sudo usermod -aG sudo <username>
```

Set `user` in [[settings.yml|First Time Install: Configuring Settings]] to your username and replace all mentions of `seed:seed` in the wiki with your `username:groupname`.

_Note: If you decide to change your username after Cloudbox install, you will need to update the service.d files with your new username/group, see [[FAQ|FAQ#error-process-xxxxx-execstopbinfusermount--uz-mntplexdrive-codeexited-status217user]]._


## 3. SSH Access

From now on, you will log into your server with the above account (not with root).

Example:
```bash
ssh seed@serveripaddress
```