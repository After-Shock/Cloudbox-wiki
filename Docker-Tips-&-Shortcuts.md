### How to stop all docker containers

```
docker stop $(docker ps -a -q)
```

### How to remove all docker containers once they are stopped (be careful)

```
docker rm $(docker ps -a -q)
```
