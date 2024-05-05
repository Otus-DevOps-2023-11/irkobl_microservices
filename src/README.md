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
docker build -t ilkor8183002/comment src/ui
docker build -t ilkor8183002/post src/ui
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
