FROM openjdk:8 as base

LABEL maintainer="NeutronStars <pro@neutronstars.fr>"

ARG version

WORKDIR /home/minecraft

RUN apt update && \
    apt install --no-install-recommends -y ca-certificates curl git && \
    curl -o BuildTools.jar https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar && \
    java -jar BuildTools.jar --rev $version && \
    mv spigot-${version}.jar server.jar

FROM openjdk:8 as release

WORKDIR /home/minecraft

ENV MC_RAM_MIN=512M
ENV MC_RAM_MAX=1G

RUN apt update && apt install --no-install-recommends -y screen

COPY minecraft/ /home/minecraft/
RUN chmod +x /home/minecraft/mc
COPY --from=base /home/minecraft/server.jar /usr/bin/

ENTRYPOINT screen -dmS server java -Xms${MC_RAM_MIN} -Xmx${MC_RAM_MAX} -jar /usr/bin/server.jar nogui && /bin/bash

EXPOSE 25565/tcp