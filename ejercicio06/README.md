# Ejercicio 06

Para poder utilzar un registry distinto en el docker file se agrega la RUTA del regsitry antes del repositorio registry.access.redhat.com/redhat-openjdk-18/openjdk18-openshift:1.12-1.1655301789 para que no lo busque por defecto en hub.docker.com

Como la imagen base de redhat levanta la aplicacion de JAVA con usuario jboss (ID 185), es que se declara en el USER 185

## Creando la imagen de Docker
Para esto se ejecuta el siguiente comando:

    docker build -t passwordapi:2-redhat-balanz .

## Corriendo la imagen creada 
Para esto se ejecuta el siguiente comando:

    docker run -p 8080:8080 passwordapi:2-redhat-balanz

## Etiquetando la imagen de Docker
Para esto se ejecuta el siguiente comando:

docker image tag passwordapi:1-redhat-balanz gustavomatsunaga/passwordapi:2-redhat-balanz

## Publicando la imagen de Docker
Para esto se ejecuta el siguiente comando:

    docker image push gustavomatsunaga/passwordapi:2-redhat-balanz

La imagen publicada en hub.docker.com es:

https://hub.docker.com/repository/docker/gustavomatsunaga/passwordapi/tags
