### TAGS:
docker run redis # pulls the latest
docker run redis:4.0 # :tag


### INPUT/TERMINAL:
```
> ./app.sh
Hello, enter your name: Rodrigo

Hello, Rodrigo!

> docker run rac2/hello-input-docker

Hello, !

> docker run -i rac2/hello-input-docker
Rodrigo

Hello, Rodrigo!

> docker run -it rac2/hello-input-docker
Hello, enter your name: Rodrigo

Hello, Rodrigo!
```

## PORT MAPPING

> docker run -p hostExternalPort:containerPortInHost image 

To add all external traffic from the host machine at port 80 will be mapped to the internal docker container running on the host at port 5000

> docker run -p 80:5000 rac2/simple-web-app

You can create different instances of the same app in different ports and serve them from the same machine
docker run -p 8080:5000 rac2/simple-web-app

## VOLUME MAPPING

If you create a db docker image, for example mysql

> docker run mysql

It will store its data inside the container at /var/lib/mysql. 

So, if we delete the container with

```
> docker stop mysql
> docker rm mysql
```

The data will go away with the container. 

A way to persist the data in the host machine is to create perform volume mapping

> docker run -v /opt/datadir:/var/lib/mysql mysql

This way the data will remain in the /opt/datadir from the mapping even when/if the container gets removed (if a new container is created, it will use the existing stored data from the system because of the volume mapping)
