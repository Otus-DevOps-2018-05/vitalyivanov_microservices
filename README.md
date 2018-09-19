# vitalyivanov_microservices
vitalyivanov microservices repository

## Homework 12 - Docker 1

- Install Docker 
- Play with the docker's commands such as `version`, `info`, `run`, `ps`, `images`, `start`, `attach`, `create`, `exec`, `commit`, `inspect`, `kill`, `stop`, `system df`, `rm`, `rmi`
- Compare `docker inspect` output for container and image 

## Homework 13 - Docker 2

- Use docker-machine to install and work with docker-engine on the GCP instance
- Create Docker image from Dockerfile

Used commands to play with docker-machine:
```sh
export GOOGLE_PROJECT=<project>
docker-machine create --driver google --google-machine-image https://www.googleapis.com/compute/v1/projects/ubuntu-os-cloud/global/images/family/ubuntu-1604-lts --google-machine-type n1-standard-1 --google-zone europe-west1-b docker-host
gcloud compute firewall-rules create reddit-app \
 --allow tcp:9292 \
 --target-tags=docker-machine \
 --description="Allow PUMA connections" \
 --direction=INGRESS
eval $(docker-machine env docker-host)
docker run --rm -ti tehbilly/htop
docker run --rm --pid host -ti tehbilly/htop
```

Used docker commands:
```sh
docker build -t reddit:latest .  
docker login  
docker tag reddit:latest zenman/otus-reddit:1.0  
docker push zenman/otus-reddit:1.0 
docker run --name reddit -d -p 9292:9292 zenman/otus-reddit:1.0
docker logs reddit -f
docker exec -it reddit bash
docker stop reddit && docker rm reddit
```
