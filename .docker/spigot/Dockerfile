FROM debian:10 as base

WORKDIR /home/minecraft

RUN apt update && \
    apt install --no-install-recommends -y ca-certificates curl && \
    curl -o server.jar https://cdn.getbukkit.org/spigot/spigot-1.8.8-R0.1-SNAPSHOT-latest.jar

FROM openjdk:8 as release

WORKDIR /home/minecraft

ENV MC_RAM_MIN=512M
ENV MC_RAM_MAX=1G

COPY minecraft/ /home/minecraft/
COPY --from=base /home/minecraft/server.jar /usr/bin

ENTRYPOINT java -Xms${MC_RAM_MIN} -Xmx${MC_RAM_MAX} -jar /usr/bin/server.jar nogui

EXPOSE 25565/tcp