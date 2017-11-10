### How to stop all docker containers

```
docker stop $(docker ps -a -q)
```

### How to remove all docker containers once they are stopped (be careful)

```
docker rm $(docker ps -a -q)
```

### Starting all but one container (e.g. All docker containers except Watchtower)

```
docker start  $(comm -13 <(docker ps -a -q --filter="name=watchtower" | sort) <(docker ps -a -q | sort))
```

### How to add your own Docker container


Add these into the docker run/create command:

```
Notes: 
- Replace all <tags> with your info.
- All <container_*> items are specified by the Docker container. 
- Ideally, you want all <name> items have the same name.
```

- `--name=<name>`
- `--network=cloudbox `
- `--network-alias=<name> `
- ` --restart=always`
- `-v /opt/<name>:<container_config_path>` 
  - This is where your config files will go.
  - You will need to:
    - create the folder: `mkdir /opt/<name>`
    - set ownership: `sudo chown -R <user>:<group> /opt/<name>`
    - set permissions: `sudo chmod g+s -R /opt/<name>`
- `-v /mnt/downloads/<name>:<container_download_path>` (if required)
  - This is where your downloaded files will go.
  - The `/mnt/downloads/<name>` path will accessible with Sonarr and Radarr. 
  - You will need to: 
    - create the folder: `mkdir /mnt/downloads/<name>`
    - set ownership: `sudo chown -R <user>:<group> /mnt/downloads/<name>`
    - set permissions: `sudo chmod g+s -R /mnt/downloads/<name>`
- `-v /etc/localtime:/etc/localtime:ro`
- `-e PGID=<your_group_ID> -e PUID=<your_user_ID>` (use command `id` to check)
- Ports:
  - For the web admin page (i.e. what nginx-proxy will redirect to; Example: 32400 for Plex):
    - `-p 127.0.0.1:<port>:<container_web_port>` 
  - For all other ports:
    - `-p <port>:<container_other_ports>` 
- `-e VIRTUAL_PORT=<container_web_port>` (same port as the one mentioned above)
- `-e VIRTUAL_HOST=<name>.<yourdomain>`
- `-e LETSENCRYPT_HOST=<name>.<yourdomain>`
- `-e LETSENCRYPT_EMAIL=<your@email.com>` 


Here are some examples: 


```
docker run -d --name=thelounge --network=cloudbox --network-alias=thelounge --restart=always -v /opt/thelounge:/home/lounge/data -v /etc/localtime:/etc/localtime:ro -e PGID=1000 -e PUID=1000 -e VIRTUAL_HOST=thelounge.domain.ml -e VIRTUAL_PORT=9000 -e LETSENCRYPT_HOST=thelounge.cloudbox.media -e LETSENCRYPT_EMAIL=your@email.com -p 127.0.0.1:9001:9000 thelounge/lounge:latest
```

```
docker run -d --name=nextcloud --network=cloudbox --network-alias=nextcloud -e 'VIRTUAL_HOST=nextcloud.domain.ml' -e 'VIRTUAL_PORT=80' -e 'LETSENCRYPT_HOST=nextcloud.domain.ml' -e 'LETSENCRYPT_EMAIL=your@email.com' -p '127.0.0.1:4674:80' -v '/opt/nextcloud:/var/www' nextcloud
```



### Watchtower

Tool to update Docker images and containers. 

NOTE: This is just for images, the apps themselves can be updated from within  their webui- please note, when running watchtower - you will loose any custom changes, e.g. nzbget updated to testing branch from within the webui - when the image is updated, it will become the previous - this is only recommended if you made no changes that could break, e.g. master DB to beta DB will break when back to master DB - so use this sparingly, if atall!

RUN AT YOUR OWN RISK!



```
docker start watchtower && docker logs -f watchtower
```

Wait 15 secs for it to finish updating all images except rutorrent (it ignores).. then:

```
docker stop watchtower
```

If no updates, stop anyway.

