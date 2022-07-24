# Ejercicio 04

Antes crear el Dockerfile escogemos una imagen Base. En mi caso elijo amazoncorretto porque tiene licencia de uso gratuita para aplicaciones comerciales.

## Creando la imagen de Docker
Para esto se ejecuta el siguiente comando:

    docker build -t passwordapi:2-jre-balanz .       

## Corriendo la imagen creada 
Para esto se ejecuta el siguiente comando:

    docker run -p 8080:8080 passwordapi:2-jre-balanz

## Etiquetando la imagen de Docker
Para esto se ejecuta el siguiente comando:

docker image tag passwordapi:2-jre-balanz gustavomatsunaga/passwordapi:2-jre-balanz

## Publicando la imagen de Docker
Para esto se ejecuta el siguiente comando:

    docker image push gustavomatsunaga/passwordapi:2-jre-balanz

La imagen publicada en hub.docker.com es:

https://hub.docker.com/repository/docker/gustavomatsunaga/passwordapi/tags
