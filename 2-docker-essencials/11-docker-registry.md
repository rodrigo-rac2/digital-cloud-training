# Docker registry

## Default registry:
> docker.io

## Pull image 'postgres'
> docker pull postgres

## Complete registry for the command above:
> docker pull docker.io/postgres/postgres

## Meaning:
registry/user_account/image

if not specified, docker assumes default registry and user account to be the same as the repository name

So, by default, we can skip specifying the repo if the image is the same name as the repo

> docker run rac2

## To run a local registry

```bash
  docker run -d -p 5000:5000 --name registry registry:2

  docker image tag my-image localhost:5000/my-image

  docker push localhost:5000/my-image

  docker pull localhost:5000/my-image

  docker pull 192.168.100:5000/my-image (corporate network)
```
