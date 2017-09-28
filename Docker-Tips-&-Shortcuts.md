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

