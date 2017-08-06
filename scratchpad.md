
readme:

just mention
Nginx-Proxy & Letsencrypt Companion
or
Nginx & Letsencrypt
idk
they are 2 containers
so link them liek we thought





Generate plex_autoscan config autom
----------------

git pull cloudbox

sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
	  
helpful docker shortcuts:
Here are some handy shortcuts.
List all containers (only IDs) docker ps -aq.
Stop all running containers. docker stop $(docker ps -aq)
Remove all containers. docker rm $(docker ps -aq)
Remove all images. docker rmi $(docker images -q)

------
NOTE FOR HETZNER SLOW IPV6 / FAILED INSTALLS:
https://unix.stackexchange.com/a/100887

netdata will use the same password set as traefik!!!!!!!!!!!!!!!!!!!!!!!

_!!_!__!_!
MAKE SURE IF YOU MOVE SERVER, /opt/traefik is completed backed up as your SSL Cert keys are there. if you move without this being backed up/restored. your subdomains will have problems until the certs expire
_!_!_!_!__!
-----------!_-------!--------!----------

PLEX:

DONT USE /tmp as transcode location. On reboots /tmp is cleared, this causes docker to create the folder as root, causing issues for plex to start transcoding! - /tmp should NEVER be used with cloudbox unless you never plan on restarting.

-----------!_-------!--------!----------


seed:password123 = default pass

sonarr and radarr::
the default install will replace nzbget categories to sonarr & radarr, sonarr/radarr must have the category set to that when adding the download client to sonarr or radarr

Note:

All containers use their container name and container port. so to setup sonarr to talk with rutorrent, you would use host http://rutorrent:80 or http://nzbget:6789 for nzbget

---- IMPORTANT NOTE -----
	IF YOU CLONED THE SCRIPT AS USER_X AND INSTALL AS USER_Y 
	YOU MUST MOVE THE CLOUDBOX DIRECTORY TO THAT USERS HOMEFOLDER AFTER INSTALLATION.
	VERY IMPORTANT!
	
	STEPS - RUN AS USER_Y: 
	
	cp /home/USER_X/cloudbox /home/USER_Y -R
	sudo rm -rf /home/USER_X/cloudbox
--------------------------

printf "Jane:$(openssl passwd -1 V3RySEcRe7)\n" >> .htpasswd
that will generate a .htpasswd
with Jane as user, and V3RySEcRe7 as password
user has todo that in /opt/rutorrent/nginx
then
http://i.imgur.com/cBlxVEx.png

add that to the nginx.conf, then docker restart rutorrent
and voila

note:::
this script has not been designed to run remotely. it has been designed to solely run from localhost. you are welcome to mess with it to support remote installs, however again, you are on your own.


note:

during install you will be asked for the plex claim token. when you paste it, you will see nothing. but this is ok, just paste the claim token and press enter


---

jackett: disable automatic updates
- blackhole does NOT function with this setup (it might but the torrents will be saved until container is next restarted)

-- 

rclone:
	have an existing rclone.conf, no worries, after installation, drop it into /opt/rclone named rclone.conf - the user that you set in settings.yml will then beable to use it without issue

	
ADVISORY NOTE: (desimaniac confirmed this works without doing this, but still might be wise to consider doing it if it fails to import their real db)
sonarr is on develop branch
radarr is on nightly branch
if you want to import an existing database, make sure you upgrade it on a working installation first, then backup, then import

on fresh setups it is worth noting that the user should go to their settings -> general tab for sonarr and radarr and set the branch to develop/nightly so that the system update tab is in sync. it defaults to master/develop i believe.
it makes no difference, but nice to see how far the container image is behind 

plexdrive :
-------

if /opt/plexdrive/token.json does not exist, then the first steps of this script will be to visit link given and paste the code given by google. plexdrive will then also be automatically setup + ran.


nzbget + rutorrent:

nzbget: MainDir must be set to /downloads/nzbget
nzbget: change the default user/password ALSO remember to set CONTROL user / password to restrict API access to authorized users.
rutorrent: any rtorrent changes must be set in the rtorrent.rc file if the user wants them to persist. default download dir has been set and some other changes to rtorrent.rc on first install.
nzbhydra: when adding a downloader, use redirect to indexer instead of proxy nzb (it mite work otherwise but again, nzbs will persist until the container is next restarted)

plex autoscan:
preconfigured for fresh installations using cloudbox. - caveats are that it is presetup for Movies as Section ID 1 and TV as Section ID 2 (meaning if fresh plex installation you must first add your Movie library then TV library second). 
If the user wishes to have trash emptying then he must manually go to /opt/plex_autoscan/config and edit config.json with his plex token, then sudo systemctl restart plex_autoscan.
Also this will NOT work if the library is empty (which it will be on a default setup) - the user must do a manual scan so that the tv and movie library has atleast 1 item in both sections, otherwise the plex cli scanner doesnt want to run...
User must also add the connection to his sonarr/radarr settings. remember to disable onGrab and onRename (onRename sends no useful info that we can use to scan with).

unionfs_cleaner:
presetup for a fresh cloudbox installation. the user must add their remote to rclone with the name of "google" - if he does not, then he must edit the existing unionfs_cleaner/config.json to the correct values for his setup.
 
 
backup:
it is suggested that plex is NOT running when this is done to prevent the sqlite database from potentially getting corrupted. although this is upto you. 
stop_plex MUST be false when using feeder type (there is no plex). backup will fail otherwise.
cron_time can be the following:
reboot
yearly
annually
monthly
weekly
daily
hourly

You can use hourly, but i would not recommend it as this task could take some time and you dont want lots of failed backups. (the script wont run when another backup is in progress thanks to backup.lock being created/removed during this process)

cron_state can be absent or present only. absent will remove any existing backup schedule. present will ensure it is always scheduled.

important note: cron is only scheduled after the backup tag has been used. if you want to disable the cron too, you must edit the settings.xml (cron_state to absent) then run the backup and it will remove from cron the scheduled task - or ensure it is there whenever a backup is ran.
note: you can manually remove the cron if wanted so you dont have to run the backup, just ensure you set the cron_state to absent aswell otherwise it will be readded next time you manual backup.

very important note, for rsync backups, ensure your rsync_dest and tgz_dest backup settings DO NOT HAVE A TRAILING SLASH OR IT WILL FAIL.
same goes for rclone, although it may be more fault tolerant, but better to leave the trailing / off all backup path settings


restore:

if the system is a fresh system without rclone, in order for this feature to work to work with use_rclone, you MUST place your rclone.conf inside the same folder as cloudbox.yml. cloudbox will then install rclone, import your .conf then restore /opt from the cloudbox.tgz stored on your remote.
restore will only work with one of rclone or rsync. rclone has priority. if both are enabled then only rclone will be used to retrieve the cloudbox.tgz and restore.
the process is simply install ansible, clone cloudbox, place rclone.conf into cloudbox directory with cloudbox.yml. sudo ansible-playbook cloudbox.yml --tags restore then use the --tags full/feeder/plex whichever you wish to be restored

***** NOTE**********:

Backup and restore does NOT backup any cloudbox settings, e.g. settings.yml - the user MUST keep a copy of this for themselves so they can drop it in along with their rclone.conf (if using rclone backup/restore) before running a restore.

If doing a restore, the user MUST create the user before running a restore otherwise their settings.yml will cause an issue (the user doesnt exist, so it cant chown)

sudo useradd -m USER
sudo passwd USER
sudo usermod -aG sudo USER


*********************

jackett:
make sure to disable auto update. watchtower will update the container for us when theres a new image

plex:

disable DLNA and advertising of ip on entwork
disable chapter thumbnail generation
disable trailers


WHOLE PACKAGE:

Dont perform manual updates via the webtools (sonarr/radarr etc...) watchtower will monitor the docker repo's for updates and autoamtically update them.

organizr:

container ip's on the cloudbox network (for use by organizr in the edit homescreen tab) for local installs
watchtower: 172.18.0.5
traefik: 172.18.0.6 : 8080
netdata: 172.18.0.7 : 19999
organizr 172.18.0.8 : 80
nzbget 172.18.0.9 : 6789
rutorrent 172.18.0.10 : 3111
jackett 172.18.0.11 : 9117
nzbhydra 172.18.0.12 : 5075
sonarr 172.18.0.13 : 8989
radarr 172.18.0.14 : 7878
plex 172.18.0.15 : 32400
plexpy 172.18.0.16 8181
plexrequests 172.18.0.17 : 3000
portainer 172.18.0.18 : 9000

organizr must point to /home for plexpy, e.g. http://plexpy:8181/home

organizr custom theme css:
https://pastebin.com/raw/vG2TgSe3