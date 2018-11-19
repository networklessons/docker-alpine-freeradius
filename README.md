# About

A simple image that runs freeradius on [Alpine](https://hub.docker.com/_/alpine).

# How to use

Configure the *clients.conf* and *users* files before you start the container. You can find examples in the [repository](https://github.com/networklessons/docker-alpine-freeradius).

## Docker run

```
docker run \
-p 1812:1812 \
-p 1813:1813 \
-v /home/vmware/docker-alpine-freeradius/clients.conf:/etc/raddb/clients.conf \
-v /home/vmware/docker-alpine-freeradius/users:/etc/raddb/users \
--name freeradius \
networklessons/docker-alpine-freeradius
```

## Docker-compose

```
version: '2'
services:
 freeradius:
  image: networklessons/docker-alpine-freeradius
  ports:
   - 1812:1812/udp
   - 1813:1813/udp
  volumes:
   - "./clients.conf:/etc/raddb/clients.conf"
   - "./users:/etc/raddb/users"
```

## Kubernetes

You can find the deployment, config-maps, and services to run this container in the kubernetes folder in the repository.