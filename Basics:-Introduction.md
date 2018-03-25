# What is Cloudbox?

- [Cloudbox](https://www.cloudbox.rocks) is an [Ansible](https://www.ansible.com/how-ansible-works) playbook based project that automates the deployment of a [docker](https://www.docker.com/what-container)-based cloud media server stack. Primary functions are: the automatic acquisition of media, storing that media on the cloud, and the ability to play your media from anywhere. 


# Why use Cloudbox? 

### Custom Domains

- Have your server setup own your own domain (e.g. app.domain.com).

### Fast Deployment

- Have a system running within minutes with minimal input. 

### Docker-Based Applications

- Docker containers keep your apps isolated from each other - no more conflicts between apps. 

- Docker containers keep your system tidy since none on of the apps' files (executables and dependencies) are stored outside of the container. 

- Quickly install and uninstall apps. 

- Configuration files for all key applications are conveniently stored in /opt, which makes backup so easy. Easily pack up your server and move to another one with Cloudbox's built-in Backups feature. 


### Cloud Storage Powered by Google Drive

- Unlimited Storage with Google Drive (Gsuites). 

 
### Can Choose Your Preferred Media Server Application

- You can decide whether to use Plex or Emby.

### Custom Server Deployment

- You can make your Cloudbox a Fullbox (i.e. both a downloading and sharing machine), or if you want to have a dual server solution, a Feederbox (i.e. downloading only) and Plexbox/Embybox (i.e. sharing media).

### Secure

- Cloudbox uses secure HTTPS powered by Let's Encrypt SSL certificates.


# How does Cloudbox function ?

[Plexdrive](https://github.com/dweidenfeld/plexdrive) will mount your Google Drive on to the server. 

UnionFS will merge the mounted Google Drive folder with your server's local folder, and this will be accessible by the media server application (e.g. Plex). 

[Sonarr](https://sonarr.tv/) will download your favorite TV Shows. [Radarr](https://radarr.video/) will download favorite movies. Both do this by utilizing either Usenet (via [NZBGet](https://nzbget.net/)) and/or Torrents (via [ruTorrent](https://github.com/Novik/ruTorrent)).<sup name="a1">[\[1\]](#f1) </sup><sup name="a2">[\[2\]](#f2)</sup> 

Sonarr / Radarr will move these downloads to your server's `/mnt/local/Media/` folder and send a notification to _Plex Autoscan_. 

[Plex AutoScan](https://github.com/l3uddz/plex_autoscan/), in turn, will tell Plex to scan for the newly downloaded TV Show or Movie, by only scanning the season / movie folders. This will (1), make the media appear in Plex sooner than what a full library scan would have been able to do, and (2), reduce the chances of Google API bans. 

[UnionFS Cleaner](https://github.com/l3uddz/unionfs_cleaner/) will eventually move the local media, that was downloaded by Sonarr / Radarr, to Google Drive, under a folder called `/Media`. The media will still be accessible by Plex via UnionFS/Plexdrive. 




![](http://i.imgur.com/xVR28pn.png)





***

<sup><b name="f1">[1](#a1)</b> Some of the applications above can be replaced by similar apps. </sup>

<sup><b name="f2">[2](#a2)</b> If you want to use Torrents, it is recommended you be a member of a private tracker vs using public ones. If you want to to use Usenet, you will need to purchase Usenet provider service (or multiple services) and also be a member of a Usenet indexer site. </sup>