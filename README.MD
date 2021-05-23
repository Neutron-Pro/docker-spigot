# Docker Image for Minecraft server 1.8

## Installation

```bash
docker-compose up -d --build
```

```bash
docker-compose down
```

- Accept Eula in the minecraft folder
- Change settings in the server.properties file (DON'T TOUCH server-port)
- You can now restart the container

## Start

```bash
docker-compose up -d
```

## Perform a minecraft command

```bash
docker attach <docker-name>
```

- You can now perform minecraft commands.

```bash
# Detach console:
CTRL+P CTRL+Q
```

## Stop

```bash
docker attach <docker-name>
stop
CTRL+P CTRL+Q
docker-compose down
```

## Build multiple container

From the docker-compose
  - Remove volumes key and value.
  - Modify ports values:

```yml
ports:
  - 25565-25565
```

Perform the docker-compose command

```bash
docker-compose up --scale spigot=[Container count] -d
```