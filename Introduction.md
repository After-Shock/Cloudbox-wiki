WORK IN PROGRESS


# What is Cloudbox ?

Cloudbox is an [Ansible](https://www.ansible.com/how-ansible-works) playbook based project that automates the deployment of a [docker](https://www.docker.com/what-container)-based cloud media server stack. Primary functions are: the automatic acquisition of media, it's long term storage, and the ability to view it from anywhere. 



# How does Cloudbox function ?

First 

It is designed for use with a Google Drive unlimited account for long term storage of your media, which can then be streamed via Plex along with any temporary local content that is awaiting being uploaded.

One of the key advantages to using Cloudbox is the fact that all the key applications are containerized in Docker containers. This gives you the ability to perform backups. These backups will include all your settings/metadata associated with them (e.g. sonarr/radarr/plex librarys+images+watched status). This will allow you to then deploy your existing setup simply via restoring the backup file then running the cloudbox installer again, and everything is how it was at the time of backup. 

Seeding content is not backed up, although the rtorrent session data is, so if you also would like rtorrent to continue seeding on the fresh system, you would need to move that seeding content across also so when rtorrent starts up, the data is there for it to continue seeding.



----\



This is not aimed at being a seedbox, although it has that capability if you dont mind using rutorrent.

The goal of this project was to be an automated cloud media server (plexdrive,unionfs, plex, sonarr/radarr/nzbget/rutorrent) with automated uploading of local data to google so you can have e.g. 100 TB plex library with only a 1TB local disk. It uses docker containers for as much as possible which gives it the rather nice ability of being able to perform backups that can be then restored on a fresh system with everything as it was (all sonarr/radarr/plex metadata intact, domain ssl certs, all settings intact etc...), the only exception to this is seeding content, although rutorrent session data will persist, you would need to manually backup/restore seeding content if you also wanted that to be on the new server.

The wiki is virtually complete, although there are some bits that need finishing. If you want to know more, it would be wise to read through the wiki to get a bit of a better understanding.



- written workflow

- image of workflow

image workflow:

http://i.imgur.com/xVR28pn.png-


