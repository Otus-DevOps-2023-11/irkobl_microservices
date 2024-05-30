# 18.Сетевое взаимодействие Docker контейнеров. Docker Compose. Тестирование образов


```bash
# Create network
docker network create back_net --subnet=10.0.2.0/24
docker network create front_net --subnet=10.0.1.0/24
```

```bash
# Run images
docker run -d --network=front_net -p 9292:9292 --name ui ilkor8183002/ui:1.0 
docker run -d --network=back_net --name comment ilkor8183002/comment:1.0
docker run -d --network=back_net --name post ilkor8183002/post:1.0
docker run -d --network=back_net --name mongo_db --network-alias=post_db --network-alias=comment_db mongo:latest
```

```bash
# Connect to the network
docker network connect front_net post
docker network connect front_net comment
```

## Network for container (bridge)

```bash
docker network ls
```
![Network](https://github.com/irkobl/picture/blob/main/docker/docker%20network%20ls.png)

```bash
ifconfig | grep br
```
![Network breadge](https://github.com/irkobl/picture/blob/main/docker/%20ifconfig%20%7C%20grep%20br.png)

```bash
brctl show br-c6a522da3b1e
```
![Breadge interface](https://github.com/irkobl/picture/blob/main/docker/brctl%20show%20br-c6a522da3b1e.png)

```bash
sudo iptables -nL -t nat
```
![Rule iptables](https://github.com/irkobl/picture/blob/main/docker/sudo%20iptables%20-nL%20-t%20nat.png)

## Composer file

```bash
# Clean workspace
docker kill $(docker ps -q)
docker network rm front_net
docker network rm back_net
docker container prune --force

# Start with docker-compose
docker-compose up -d
```

```bash
docker-compose ps
```
![Running](https://github.com/irkobl/picture/blob/main/docker/docker-compose%20ps.png)

```bash
docker ps -a
```
![Container](https://github.com/irkobl/picture/blob/main/docker/docker%20ps%20-a.png)

### UI Dashboard
![UI](https://github.com/irkobl/picture/blob/main/docker/Screenshot%20from%202024-05-11%2020-58-44.png)



# 17.Docker образы. Микросервисы 

## Start images

```bash
# Network 
docker network create reddit
# Volume
docker volume create reddit_db

cd irkobl_microservices

# BUild Images
docker pull mongo:latest
docker build -t ilkor8183002/comment src/comment
docker build -t ilkor8183002/post src/post-py
docker build -t ilkor8183002/ui:2.0 src/ui

# Run images with network alias and local volume
docker run -d --network=reddit \
 --network-alias=post_db_post --network-alias=comment_db_coment -v reddit_db:/data/db mongo:latest
docker run -d --network=reddit \
 --network-alias=post ilkor8183002/post:1.0
docker run -d --network=reddit \
 --network-alias=comment ilkor8183002/comment:1.0
docker run -d --network=reddit \
 -p 9292:9292 ilkor8183002/ui:2.0

```
