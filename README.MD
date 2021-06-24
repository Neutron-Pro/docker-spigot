# Docker Image for Minecraft server 1.8

## Installation

- Change settings in the ./docker/spigot/minecraft/server.properties file (DON'T TOUCH server-port) and yml configuration
- place your world in ./docker/spigot/minecraft folder (no require)

```bash
docker-compose up -d --build
```

## Start

```bash
docker-compose up -d
```

## Perform a minecraft command

```bash
docker exec -it spigot sh mc <Minecraft Command>
```

## Stop

```bash
docker exec -it spigot sh mc stop
docker-compose down
```

## Build multiple container

From the docker-compose
  - Remove volumes key and value.
  - Remove the container_name key.
  - Modify ports values:

```yml
ports:
  - 25565-25565
```

Perform the docker-compose command

```bash
docker-compose up --scale spigot=[Container count] -d
```