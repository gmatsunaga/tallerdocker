## Instalacion de dive para Docker

    docker pull wagoodman/dive

## Obteniendo Capas de JAVA8 ALPINE
Obteniendo las capas con docker inspect:

    docker inspect nicopaez/passwordapi-java:java8-alpine

Vemos que la imagen nicopaez/passwordapi-java:java8-alpine tiene 4 capas:

"Layers": [
    "sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c",
    "sha256:298c3bb2664fb7f8514ecdde8b76c0ca95c7c7b82eaa326a7e9661e017488164",
    "sha256:8bc7bbcd76b68a51a3b70de9f19faed58f9c0795802dbff98de584b7e7eb9c22",
    "sha256:07f83dc33f640a098b67a7587dfc42f0e91f3b21aa08a7a02e613edca4901e22"
]

De igual manera utilziando dive:

    docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock wagoodman/dive:latest nicopaez/passwordapi-java:java8-alpine
  
Vemos La imagen nicopaez/passwordapi-java:java8-alpine tiene 4 capas:

4.4 MB FROM 8f52818719ad48a
87 B { echo '#!/bin/sh'; echo 'set -e'; echo; echo 'dirname "$(dir
79 MB set -x && apk add --no-cache openjdk8-jre="$JAVA_ALPINE_VERSION" && [ "$JAVA_
25 MB #(nop) COPY file:a6e9b80e7469da50e389566bffb8669b6e40df0caeaf327465fb3d0162788101 in /app.jar

## Obteniendo Capas de JAVA8 FABRIC
Obteniendo las capas con docker inspect:

    docker inspect nicopaez/passwordapi-java:java8-fabric

Vemos que la imagen nicopaez/passwordapi-java:java8-fabric tiene 9 capas:

"Layers": [
    "sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c",
    "sha256:7884dc8a73eb153770c61d327c027df411ea035bb2292a0a75373481a4b7fbd0",
    "sha256:717d137b16f996bf59af63c2abfd89b69faec166381549203c1439d6fdc6ddf2",
    "sha256:b85e653858e97c56eedb2e19e225c482cbad71fd54f90059c0da3c2dc58713cf",
    "sha256:f42a66141db68550a56f7b8c4cd9e2f0127d94accfe77e124f4b68999e9374b3",
    "sha256:ad275ed181794a5e37d0b3964e23ecedbd272a03ba26215f8d83de65e27436a3",
    "sha256:dd69ad62f09595f6c7ffa79438b9e7b3f0135a8d8d3e425c1bc37c8a70abc635",
    "sha256:8bef50a12deaffef57f54aaf2facddce8c04ea9253efe8afd33c44b7d0fc2f8e",
    "sha256:b4b541fa416f1d2f1d983b11c28cb1a91e3c09167cabb0cfd29fcdeb2239721c"
]

De igual manera utilziando dive:

    docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock wagoodman/dive:latest nicopaez/passwordapi-java:java8-fabric
 
Vemos que la imagen nicopaez/passwordapi-java:java8-fabric tiene 9 capas:

4.4 MB FROM 8f52818719ad48a
0 B mkdir -p /deployments
99 MB apk add --update curl openjdk8=8.171.11-r0 && rm /var/cache/apk/* && echo "securerandom.source=file:/dev/urandom"
4.0 kB #(nop) ADD file:0e4d47c8ceb53292ec2698ca6f70c3f2954e747263a46f1b6b1fa70f71d9d9d4 in /opt/run-java-options
869 kB mkdir -p /opt/agent-bond && curl http://central.maven.org/maven2/io/fabric8/agent-bond-agent/1.2.0/agent-bond-agent-1.2.0.
919 B #(nop) ADD file:19cf38fb1c34ab0ebb2252bb70ed3ea973b69d12e67d2ef36785bb6efa0eb9f4 in /opt/agent-bond/
19 kB #(nop) COPY file:9664759840f7d23e79c24ae404fe981e8256b6c5145da410f07b11767f9366e3 in /deployments/
19 kB chmod 755 /deployments/run-java.sh
25 MB #(nop) COPY file:a6e9b80e7469da50e389566bffb8669b6e40df0caeaf327465fb3d0162788101 in /deployments/app.jar


## Conclusiones
 
Comparando capas de ambas imagenes nicopaez/passwordapi-java:java8-alpine y nicopaez/passwordapi-java:java8-fabric vemos que solo tiene en comun la primera capa:

"sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c" que ocupa 4.4MB



 



