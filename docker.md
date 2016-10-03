# History

```bash
docker run docker/whalesay cowsay boo
docker build -t docker-whale .
docker run docker-whale
docker tag beee45d79591 skocic/docker-whale:latest
docker login --username=skocic --email=skocic@goodgamestudios.com
docker push skocic/docker-whale
docker rmi -f beee45d79591
docker rmi skocic/docker-whale
docker run skocic/docker-whale
docker images
docker ps
docker run -i -t alpine /bin/sh
docker commit 88389a2ff148 skocic/broken-alpine
docker run -i -t skocic/broken-alpine
docker push skocic/broken-alpine
docker composer up
docker run -p 8080:8080 -p 50000:50000 --name jenkins -v ~/workspace/jenkins:/var/jenkins_home -d --restart=always jenkins
```

# Install

## CentOS

```bash
sudo curl -fsSL https://get.docker.com/ | sh
sudo usermod -aG docker ggs
sudo service docker start
```
logout and login and try

    docker run hello-world

# Examples

From https://docs.docker.com/linux/step_one/

```bash
docker run docker/whalesay cowsay boo
docker images
mkdir mydockerbuild
cd mydockerbuild
vi Dockerfile
```

	Dockerfile
```Dockerfile
FROM docker/whalesay:latest
RUN apt-get -y update && apt-get install -y fortunes
CMD /usr/games/fortune -a | cowsay
```

```bash
docker build -t docker-whale .
docker run docker-whale
docker tag beee45d79591 skocic/docker-whale:latest
docker login --username=skocic --email=skocic@goodgamestudios.com
docker push skocic/docker-whale
docker rmi -f beee45d79591
docker rmi skocic/docker-whale
docker run skocic/docker-whale
```

https://www.docker.com/products/docker-toolbox

[Introduction to Docker](https://www.youtube.com/watch?v=Q5POuMHxW-0)

```bash
docker run -i -t alpine /bin/sh
rm -rf /var
[ggs@localhost:/var/www/goodgamestudios.com/paymentbackend]$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
88389a2ff148        alpine              "/bin/sh"           45 seconds ago      Up 43 seconds                           admiring_poitras
[ggs@localhost:/var/www/goodgamestudios.com/paymentbackend]$ docker diff 88389a2ff148
C /root
A /root/.ash_history
D /var
[ggs@localhost:/var/www/goodgamestudios.com/paymentbackend]$ docker commit 88389a2ff148 skocic/broken-alpine
903cc26ef80043ac2f34ed0f198e6e807e1395e3db2177abc181e5c46b73c878

docker commit 88389a2ff148 skocic/broken-alpine
docker run -i -t skocic/broken-alpine
docker push skocic/broken-alpine
The push refers to a repository [skocic/broken-alpine] (len: 1)
903cc26ef800: Image already exists
6c3749c1a1f0: Image successfully pushed
07a21b5aad0d: Image successfully pushed
c5572343789c: Image successfully pushed
548d27a98ab4: Image successfully pushed
0971e2657337: Image successfully pushed
2a250d324882: Image successfully pushed
Digest: sha256:b23e3575f13434f4ff7a06ef6e3b814f0391ef90d0eef400d7b76554f862483f

```
[Search broken-alpine](https://hub.docker.com/search/?isAutomated=0&isOfficial=0&page=1&pullCount=0&q=broken-alpine&starCount=0)

```sh
docker run -p 8080 -i -t alpine /bin/sh
apk update
apk add netcat-openbsd
nc -l 8080
curl localhost:32768
```

```
/ # nc -l 8080
GET / HTTP/1.1
User-Agent: curl/7.19.7 (x86_64-redhat-linux-gnu) libcurl/7.19.7 NSS/3.19.1 Basic ECC zlib/1.2.3 libidn/1.18 libssh2/1.4.2
Host: localhost:32768
Accept: */*
```

## Notes

zsh, [diamond](https://github.com/lgs/diamond), ldap, splunk, ssh
LXC, go, node.js, ruby
cookbook, dependencies, flavours
golang, alpine

apk add --no-cache git
alpine model compiling

## Install Docker Compose

https://docs.docker.com/compose/install/

```bash
curl -L https://github.com/docker/compose/releases/download/1.7.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker composer up
``````

# Docker-machine

```bash
docker-machine create --driver=virtualbox vbox-test
docker-machine env vbox-test
docker-machine ssh vbox-test

unset ${!DOCKER_*}
eval $(docker-machine env default)
```

## centos-6.6-x86-64-desktop-pb

```sh
docker build -t centos-6.6-x86-64-desktop-pb .
docker run -i -t --entrypoint /bin/bash centos-6.6-x86-64-desktop-pb
```

## Minecraft

```bash
docker run -d -it -p 25565:25565 --name mc -e VERSION=1.8.9 -v /home/user/docker/minecraft/data:/data -e EULA=true -e OPS=Hikupz -e ALLOW_NETHER=true -e ANNOUNCE_PLAYER_ACHIEVEMENTS=true -e ENABLE_COMMAND_BLOCK=true -e ENABLE_COMMAND_BLOCK=true -e GENERATE_STRUCTURES=true -e SPAWN_ANIMALS=true -e SPAWN_MONSTERS=true -e SPAWN_NPCS=true -e MODE=survival -e MODPACK=https://www.spigotmc.org/resources/ride-a-mob-beta.29983/download?version=117160 itzg/minecraft-server
```

Get uuid from http://minecraft-techworld.com/uuid-lookup-tool

Edit `/data/ops.json` and add highest op level to your username
```json
[
  {
    "uuid": "f4d5e84d-8f41-4934-b43e-38cce424aaf3",
    "name": "Hikupz",
    "level": 4
  }
]
```

# Jenkins

```bash
docker run -p 8080:8080 -p 50000:50000 --name jenkins -v ~/workspace/jenkins:/var/jenkins_home -d --restart=always jenkins
```
