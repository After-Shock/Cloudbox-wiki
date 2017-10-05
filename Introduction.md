- written workflow

- image of workflow

image workflow:

http://i.imgur.com/xVR28pn.png

---

Cloudbox is an ansible playbook to automate the deployment of a cloud media server stack. It is designed for use with a Google Drive unlimited account for long term storage of your media, which can then be streamed via plex along with any temporary local content that is awaiting being uploaded.

One of the key advantages to using cloudbox is the fact that all the key applications are containerised (docker). This gives you the ability to perform backups. These backups will include all your settings/metadata associated with them (e.g. sonarr/radarr/plex librarys+images+watched status). This will allow you to then deploy your existing setup simply via restoring the backup file then running the cloudbox installer again, and everything is how it was at the time of backup. 

Seeding content is not backed up, although the rtorrent session data is, so if you also would like rtorrent to continue seeding on the fresh system, you would need to move that seeding content across also so when rtorrent starts up, the data is there for it to continue seeding.