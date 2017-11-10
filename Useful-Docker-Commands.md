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

### How to install your custom Docker container


Add these into the docker run/create command (replace all <> with your info):

- `--name=<name>`
- `--network=cloudbox `
- `--network-alias=<name> `
- ` --restart=always`
- `-v /opt/<name>:/config`
  - You also need to create this folder: `mkdir /opt/<name>`.
- `-v /etc/localtime:/etc/localtime:ro`
- `-e PGID=<your group ip> -e PUID=<your user id>` (use command `id` to check)
- `-e VIRTUAL_HOST=<name>.<yourdomain>`
- `-e LETSENCRYPT_HOST=<name>.<yourdomain>`
- `-e LETSENCRYPT_EMAIL=<your@email.com>` 
- Ports:
  - For the web admin page (i.e. what nginx-proxy will redirect to; Example: 32400 for Plex):
    - `-e VIRTUAL_PORT=<port>`
    - `-p 127.0.0.1:<port>:<port>` 
  - For all other ports:
    - `-p <port>:<port>` 


Here are some examples: 


```
docker run -d --name=thelounge --network=cloudbox --network-alias=thelounge --restart=always -v /opt/thelounge:/home/lounge/data -v /etc/localtime:/etc/localtime:ro -e PGID=1000 -e PUID=1000 -e VIRTUAL_HOST=thelounge.domain.ml -e VIRTUAL_PORT=9000 -e LETSENCRYPT_HOST=thelounge.cloudbox.media -e LETSENCRYPT_EMAIL=your@email.com -p 127.0.0.1:9001:9000 thelounge/lounge:latest
```

```
docker run -d --name=nextcloud --network=cloudbox --network-alias=nextcloud -e 'VIRTUAL_HOST=nextcloud.domain.ml' -e 'VIRTUAL_PORT=80' -e 'LETSENCRYPT_HOST=nextcloud.domain.ml' -e 'LETSENCRYPT_EMAIL=your@email.com' -p '127.0.0.1:4674:80' -v '/opt/nextcloud:/var/www' nextcloud
```

