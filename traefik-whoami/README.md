# Traefik-Whoami Prototype

_This is a mini protype running on Docker engine, using docker-compose to launch a Traefik proxy and a go-based dumb web app Whoami._

To understand more about Traefik: https://youtu.be/AqiGcLsVMeI  
Traefik documentation: https://doc.traefik.io/traefik/

## Pre-requisite

- Docker installed (tested with > Docker version 19.03.13, build 4484c46d9d)
- The setup is based on an external network, which needs to be created (c.f. launch procedure)
- Internet and credentials to access to https://hub.docker.com/

## Environement Variables

Environment variables are managed with .env files files are located under folder ./env/  
In this project we use one file: .env file

## Configuration Files

Configuration files are located under folder ./conf/  
In this project we use one file: traefik.yaml

# Start & Complete Shutdown

## Launch Procedure

_Create the network with the arbitrary name 'web' which will be used by Traefik and the managed services_  
`$ docker network create web`

_Create the containers and launch the services as defined within the docker-compose file_  
`$ docker-compose --env-file ./env/.env -f docker-compose.traefik.yaml up -d`

*Un lancement reussi permet l'acces aux services suivants:*

- Dashboard Traefik http://localhost:8080/
- La page de Whoami http://whoami.localhost/

## Shudown Procedure

_Graceful shutdown of the services, removal of containers, and anything created by the the docker-compose file_  
`$ docker-compose --env-file ./env/.env -f docker-compose.traefik.yaml down`