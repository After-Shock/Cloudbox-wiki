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


Add these into the docker run/create command (replace all <> with your info; all <container_*> items are specified by the Docker container):

- `--name=<name>`
- `--network=cloudbox `
- `--network-alias=<name> `
- ` --restart=always`
- `-v /opt/<name>:<container_config_path>` 
  - This is where your config files will go.
  - You also need to create this folder: `mkdir /opt/<name>`.
- `-v /mnt/downloads/<name>:<container_download_path>` (if required)
  - This is where your downloaded files will go.
  - The `/mnt/downloads/<name>` path is accessible with Sonarr and Radarr. 
  - You also need to: 
    - create the folder: `mkdir /mnt/<name>`
    - set ownership: `sudo chown -R <user>:<group> /mnt/downloads/<name>`
    - set permissions: `sudo chmod g+s -R /mnt/downloads/<name>`
- `-v /etc/localtime:/etc/localtime:ro`
- `-e PGID=<your_group_ID> -e PUID=<your_user_ID>` (use command `id` to check)
- Ports:
  - For the web admin page (i.e. what nginx-proxy will redirect to; Example: 32400 for Plex):
    - `-p 127.0.0.1:<port>:<container_web_port>` 
  - For all other ports:
    - `-p <port>:<container_other_port>` 
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

