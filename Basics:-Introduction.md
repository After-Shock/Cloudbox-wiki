# What is Cloudbox?

- Cloudbox is an [Ansible](https://www.ansible.com/how-ansible-works) playbook based project that automates the deployment of a [docker](https://www.docker.com/what-container)-based cloud media server stack. Primary functions are: the automatic acquisition of media, storing that media on the cloud, and the ability to play your media from anywhere. 


# Why use Cloudbox? 

## Custom Domains

- Have your server setup own your own domain (e.g. app.domain.com).

## Fast Deployment

- Have a system running within minutes with minimal input. 

## Docker-Based Applications

- Docker containers keep your apps isolated from each other - no more conflicts between apps. 

- Docker containers keep your system tidy since none on of the apps' files (executables and dependencies) are stored outside of the container. 

- Quickly install and uninstall apps. 

- Configuration files for all key applications are conveniently stored in /opt, which makes backup so easy. Easily pack up your server and move to another one with Cloudbox's built-in Backups feature. 


## Cloud Storage Powered by Google Drive

- Unlimited Storage with Google Drive (Gsuites). 

 
## Can Choose Your Preferred Media Server Application

- You can decide whether to use Plex or Emby.

## Custom Server Deployment

- You can make your Cloudbox a Fullbox (i.e. both a downloading and sharing machine), or if you want to have a dual server solution, a Feederbox (i.e. downloading only) and Plexbox/Embybox (i.e. sharing media).

## Secure

- Cloudbox uses secure HTTPS powered by Let's Encrypt SSL certificates.


# How does Cloudbox function ?




`Sonarr` will acquire your favorite TV Shows and `Radarr` your favorite movies, by utilizing either Torrents (i.e `ruTorrent` and/or Usenet (i.e. `NZBGet`). `UnionFS Cleaner` will eventually move your media will to Google Drive, under a folder called `/Media`. `Plexdrive` will mount your Google Drive on to the server, so that your media server application (i.e. `Plex`, `Emby`) will be able to play it back. 

> If you want to use Torrents, it is recommended you be a member of a private tracker vs using public ones. If you want to to use Usenet, you will need to purchase Usenet provider service (or multiple services) and also be a member of a Usenet indexer site. 

> Some of the applications above can be replaced by similar apps. 


![](http://i.imgur.com/xVR28pn.png)


