## Raspberry PI Home Configuration

Dockerized services for my little raspberry pi home server.


### Services

- Portainer
- Home Assistant
- Organizr
- Sonarr
- Radarr
- Jackett
- OpenVPN + Transmission

### Manage using docker-machine

**[How to set up docker machine on raspberry PI](https://gist.github.com/tsubik/5b5e724830a2f5b6cb1a42a86e3342b6)**

Assuming the machine name is set to `home-pi` change docker env variables to point to that machine

``` shell
eval $(docker-machine env home-pi)
```

Starting up all containers

``` shell
docker-compose up -d
```
