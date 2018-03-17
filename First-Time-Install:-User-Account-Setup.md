## 1. User Account Setup

Choose **ONE** of the following:

###    i. Create a new user account `seed` (recommended)

In this step, you will create the user account `seed` and add it to the `seed` and `sudo` groups.  


Run the following commands line by line:


```bash
sudo useradd -m seed
sudo usermod -aG sudo seed
sudo passwd seed
su seed
```

_Note: If you have an existing user account that you don't plan on using, it may be a good idea to remove it and just stick with using `seed` for everything._

###    ii. Create a new user account other than `seed`

Run the following commands line by line:

```bash
sudo useradd -m <username>
sudo usermod -aG sudo <groupname>
sudo passwd <username>
su <username>
```

Set `user` in [[settings.yml|First Time Install: Configuring Settings]] to your username and replace all mentions of `seed:seed` in the wiki with your `username:groupname`.

_Note: If you decide to change your username after Cloudbox install, you will need to update the service.d files with your new username/group, see [[FAQ|FAQ#error-process-xxxxx-execstopbinfusermount--uz-mntplexdrive-codeexited-status217user]]._


###    iii. Use an existing user account

Set `user` in [[settings.yml|First Time Install: Configuring Settings]] to your username and replace all mentions of `seed:seed` in the wiki with your `username:groupname`.

_Note: If you decide to change your username after Cloudbox install, you will need to update the service.d files with your new username/group, see [[FAQ|FAQ#error-process-xxxxx-execstopbinfusermount--uz-mntplexdrive-codeexited-status217user]]._


## 2. SSH Access

From now on, you will log into your server via the above account (e.g. `ssh seed@serveripaddress). 