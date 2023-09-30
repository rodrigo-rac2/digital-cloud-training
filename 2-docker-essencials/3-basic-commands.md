## Basic docker commands
```
docker run/docker stop
docker pull # doesn't start a container with the image
docker ps -a
docker rm id or name
docker rmi image (need to remove all containers with that image first first)
docker images
```

On the terminal, for a running container:
> docker exe container-id "command" 
(like: 'cat /etc/*release*')

Can test them with the hello_world image
