# Docker Image for Minecraft server

## Installation

- Change settings in the ./docker/spigot/minecraft/server.properties file (DON'T TOUCH server-port) and yml configuration
- Place your world in ./docker/spigot/minecraft folder (no require)
- Change the version in the docker-compose.yml file. (no require)

```bash
docker-compose up -d --build
```

```diff
- Please note that the installation takes time because it uses the BuildTools of Spigot. For the version, please indicate a valid version. For more information: https://www.spigotmc.org/wiki/buildtools/
```

## Start

```bash
docker-compose up -d
```

## Perform a minecraft command

```bash
docker exec -it spigot ./mc <Minecraft Command>
```

## Stop

```bash
docker exec -it spigot ./mc stop
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