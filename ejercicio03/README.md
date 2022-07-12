## Instalacion de dive para Docker

    docker pull wagoodman/dive

## Obteniendo Capas de JAVA8 ALPINE

    docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock wagoodman/dive:latest nicopaez/passwordapi-java:java8-alpine
  

Layers:
4.4 MB FROM 8f52818719ad48a
87 B { echo '#!/bin/sh'; echo 'set -e'; echo; echo 'dirname "$(dir
79 MB set -x && apk add --no-cache openjdk8-jre="$JAVA_ALPINE_VERSION" && [ "$JAVA_
25 MB #(nop) COPY file:a6e9b80e7469da50e389566bffb8669b6e40df0caeaf327465fb3d0162788101 in /app.jar

## Obteniendo Capas de JAVA8 FABRIC

    docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock wagoodman/dive:latest nicopaez/passwordapi-java:java8-fabric
  

Layers:
4.4 MB FROM 8f52818719ad48a
0 B mkdir -p /deployments
99 MB apk add --update curl openjdk8=8.171.11-r0 && rm /var/cache/apk/* && echo "securerandom.source=file:/dev/urandom"
4.0 kB #(nop) ADD file:0e4d47c8ceb53292ec2698ca6f70c3f2954e747263a46f1b6b1fa70f71d9d9d4 in /opt/run-java-options
869 kB mkdir -p /opt/agent-bond && curl http://central.maven.org/maven2/io/fabric8/agent-bond-agent/1.2.0/agent-bond-agent-1.2.0.
919 B #(nop) ADD file:19cf38fb1c34ab0ebb2252bb70ed3ea973b69d12e67d2ef36785bb6efa0eb9f4 in /opt/agent-bond/
19 kB #(nop) COPY file:9664759840f7d23e79c24ae404fe981e8256b6c5145da410f07b11767f9366e3 in /deployments/
19 kB chmod 755 /deployments/run-java.sh
25 MB #(nop) COPY file:a6e9b80e7469da50e389566bffb8669b6e40df0caeaf327465fb3d0162788101 in /deployments/app.jar

  

## Comparando Layers
 
Entre nicopaez/passwordapi-java:java8-alpine y nicopaez/passwordapi-java:java8-fabric tiene en comun:

* La imagen Base 8f52818719ad48a0af558ae2a44eed3cb3fe080f13c9fbdc67ef15667af59196 de 4.4MB
* La capa final donde se copia el JAR de passwordapi-java de 25MB

 
