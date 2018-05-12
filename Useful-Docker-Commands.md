# Docker Commands

#### Stop all docker containers

```
docker stop $(docker ps -a -q)
```

#### Start all docker containers

```
docker start $(docker ps -a -q)
```

#### Start all but one container (e.g. All docker containers except Watchtower)

```
docker start  $(comm -13 <(docker ps -a -q --filter="name=watchtower" | sort) <(docker ps -a -q | sort))
```

#### Remove all docker containers - once they are stopped (be careful)

```
docker rm $(docker ps -a -q)
```

#### Forcefully, Remove all docker containers  (be careful)

```
docker rm -f $(docker ps -a -q)
```

#### Restart only the running containers

```
/opt/scripts/docker/restart_containers.sh
```

# Docker Logs

Find the container name: `docker ps -a`


Live log (from the beginning of the log):
```
docker logs -follow <container_name>
```

Live log (from the last 10 lines of the log):
```
docker logs --follow --tail 10 <container_name>
```

# Removing Docker Containers

Don't want a certain docker container? You can remove it with the follow steps.

_Note: Certain docker containers are essential to Cloudbox  (e.g. nginx-proxy, letsencrypt)._

Via Command line:
- Get a list of docker container's installed: `docker ps -a`  
- Remove the one you don't want (where `<name>` is replaced with the docker container's name): `docker stop <name> && docker rm <name>`

Via Portainer:
- https://portainer._yourdomain.com_
- "Containers" --> make your selection --> "Remove"





# Add your own Docker container


Add these into the docker run/create command:

```
Notes: 
- Replace all <tags> with your info.
- All <container_*> items are specified by the Docker container. 
- Ideally, you want all <name> items have the same name.
- Pick docker images that allow you to specify PUID/PGID.
- You can break a command into multiple lines with a backslash '\'
 at the end of all the lines except the last one.
```

- Basics:
  - `--name=<name>`
  - `--restart=always`
    - To have it startup automatically.
  - `-v /etc/localtime:/etc/localtime:ro`
    - To set the docker container's timezone to your host timezone.
  - `-e PUID=<your_user_ID> -e PGID=<your_group_ID>`
    - Replace `<user>` and `<group>` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid)).
- Mount Paths:

  Mount paths are in the format of `path/on/host:path/within/container`. You may change the path on host (left side), but not the path set for the container, internally (right side). 

  - `-v /opt/<name>:<container_config_path>` 
    - This is where your config files will go.
    - You will need to:
      - Create the folder: `mkdir /opt/<name>`
      - Set ownership: `sudo chown -R <user>:<group> /opt/<name>` 
        - Replace `<user>` and `<group>` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid))
      - Set permissions: `sudo chmod -R g+s /opt/<name>`
  - `-v /mnt/downloads/<name>:/mnt/downloads/<name>`
    - Only required if your Docker app needs a path for downloads.
    - You will need to set `/mnt/downloads/<name>` as the downloads path in your app.  
    - This path will be accessible to Sonarr and Radarr. 
    - You will need to: 
      - Create the folder: `mkdir /mnt/downloads/<name>`
      - Set ownership: `sudo chown -R <user>:<group> /mnt/downloads/<name>`
        - Replace `<user>` and `<group>` to match yours' (see [here](FAQ#find-your-user-id-uid-and-group-id-gid))
      - Set permissions: `sudo chmod -R g+s /mnt/downloads/<name>`
- Network (these are important): 
  - `--network=cloudbox `
  - `--network-alias=<name> `   (aliases are shortcuts to communicate across dockers)
  - Note: Leave these out if your docker run command requires `--net=host`.
- Ports:

  Ports are in the format of `host_port:container_port`. 

  Usually, you will want those two ports to match. However, since a host can only use one port number at a time, if you to create multiple containers of the same app (e.g. Radarr and Radarr4k), then you will need to change the host port (left side) to something else, but you will always leave the container port (right side) as is.

  - For the main port (i.e. the web admin page that nginx-proxy will redirect 80/443 to; example: 32400 for Plex):
    - `-p 127.0.0.1:<host_port>:<container_webadmin_port>` 
  - For all other ports:
    - `-p <host_port>:<container_other_ports>`
- Nginx Proxy Stuff:
  - `-e VIRTUAL_PORT=<container_webpage_port>` (same port as the one mentioned above)
  - `-e VIRTUAL_HOST=<name>.<yourdomain>`
  - `-e LETSENCRYPT_HOST=<name>.<yourdomain>`
  - `-e LETSENCRYPT_EMAIL=<your@email.com>`  #This should be a real email address.


Here are some examples: 


```
docker run -d  \
	--name=thelounge  \
	--restart=always  \
	-e PGID=1000 -e PUID=1000  \
	-v /opt/thelounge:/home/lounge/data  \
	-v /etc/localtime:/etc/localtime:ro  \
	--network=cloudbox  \
	--network-alias=thelounge  \
	-p 127.0.0.1:9001:9000  \
	-e VIRTUAL_HOST=thelounge.yourdomain.com  \
	-e VIRTUAL_PORT=9000  \
	-e LETSENCRYPT_HOST=thelounge.yourdomain.com  \
	-e LETSENCRYPT_EMAIL=your@email.com  \
	thelounge/lounge:latest
```

```
docker run -d \
	--name=nextcloud  \
	--restart=always \
	-v '/opt/nextcloud:/var/www'  \
	--network=cloudbox  \
	--network-alias=nextcloud  \
	-p '127.0.0.1:4674:80'  \
	-e 'VIRTUAL_HOST=nextcloud.yourdomain.com'  \
	-e 'VIRTUAL_PORT=80'  \
	-e 'LETSENCRYPT_HOST=nextcloud.yourdomain.com'  \
	-e 'LETSENCRYPT_EMAIL=your@email.com'  \
	nextcloud
```

Here is a blanked template (containers will not always use `/config`)

```
docker run -d \
    --name <name> \
    --restart=always \
    -e PGID=1000 -e PUID=1000  \
    --network=cloudbox \
    --network-alias=<name> \
    -p 127.0.0.1:<host_port>:<container_webadmin_port> \
    -p <host_port2>:<container_misc_port1> \
    -p <host_port3>:<container_misc_port2> \
    -v /opt/<name>/:/config \
    -v /mnt/:/mnt/ \
    -e VIRTUAL_PORT=<container_webadmin_port> \
    -e VIRTUAL_HOST=<name>.yourdomain \
    -e LETSENCRYPT_HOST=<name>.yourdomain \
    -e LETSENCRYPT_EMAIL=<your@email.com> \
    <docker-hub-user>/<repo-name>
```

# Misc 

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


### Plex

#### Make Plex scan a specific folder

You'll need to get the [[Plex Library Section IDs]]. 


Replace `<section ID>` and `<movie or tv show path>` in the following command:

```
docker exec -u plex -i plex bash -c 'export LD_LIBRARY_PATH=/usr/lib/plexmediaserver;/usr/lib/plexmediaserver/Plex\ Media\ Scanner --scan --refresh --section <section ID> --directory '"'"'/data/<movie or tv show path>'"'"''
```


Example: TV Show
```
docker exec -u plex -i plex bash -c 'export LD_LIBRARY_PATH=/usr/lib/plexmediaserver;/usr/lib/plexmediaserver/Plex\ Media\ Scanner --scan --refresh --section 2 --directory '"'"'/data/TV/No Activity US/'"'"''
```

Example: TV Show + specific season
```
docker exec -u plex -i plex bash -c 'export LD_LIBRARY_PATH=/usr/lib/plexmediaserver;/usr/lib/plexmediaserver/Plex\ Media\ Scanner --scan --refresh --section 2 --directory '"'"'/data/TV/El Chapo/Season 02/'"'"''
```
