### Stop all docker containers

```
docker stop $(docker ps -a -q)
```

### Remove all docker containers once they are stopped (be careful)

```
docker rm $(docker ps -a -q)
```

### Start all but one container (e.g. All docker containers except Watchtower)

```
docker start  $(comm -13 <(docker ps -a -q --filter="name=watchtower" | sort) <(docker ps -a -q | sort))
```

### Restart only the running containers

```
/opt/scripts/docker/restart_containers.sh
```

### Docker Logs

Find the container name: `docker ps -a`


Live log:
```
docker logs -f <container_name>
```


### Don't want a certain docker container?

You can remove it with the follow steps.

_Note: Certain docker containers are essential to Cloudbox  (e.g. nginx-proxy, letsencrypt)._

Via Command line:
- Get a list of docker container's installed: `docker ps -a`  
- Remove the one you don't want (where `<name>` is replaced with the docker container's name): `docker stop <name> && docker rm <name>`

Via Portainer:
- https://portainer._yourdomain.com_
- "Containers" --> make your selection --> "Remove"





### Add your own Docker container


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
    - set permissions: `sudo chmod -R g+s /opt/<name>`
- `-v /mnt/downloads/<name>:<container_download_path>` (if required)
  - This is where your downloaded files will go.
  - The `/mnt/downloads/<name>` path will accessible with Sonarr and Radarr. 
  - You will need to: 
    - create the folder: `mkdir /mnt/downloads/<name>`
    - set ownership: `sudo chown -R <user>:<group> /mnt/downloads/<name>`
    - set permissions: `sudo chmod -R g+s /mnt/downloads/<name>`
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

Note: We recommend you manually update the docker images and containers via the [[update-tags|Updating Cloudbox Apps#rebuild-the-docker-containers]]. Updating Docker containers like this has been known to cause data corruption. So use at your own risk. 

```
docker start watchtower && docker logs -f watchtower
```

Wait 15 secs for it to finish updating all images except rutorrent (it ignores).. then:

```
docker stop watchtower
```

If no updates, stop anyway.


