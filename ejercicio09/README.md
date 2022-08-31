# Ejercicio 09

## Definicio de secrets
Para crear los secrets ejecutamos estos comandos:

    echo "Passw0rd!" | docker secret create clave_db -
    echo "postgres://postgres:Passw0rd!@db:5432/postgres" | docker secret create connection_string -

Para verificar que se crearon correctamente, ejecutamos:

    docker secret ls

y nos retorna los dos secrets creados

    ID                          NAME                DRIVER    CREATED              UPDATED
    of2gxa0hzu2bturrf2lo6wf4s   clave_db                      About a minute ago   About a minute ago
    kfn5hpc315wswyhd1zb8bnomj   connection_string             4 seconds ago        4 seconds ago


## Definicion de Networks
Para comunicar el servicio web y db se especifico una network llamada backnet, en la cual ambos contenedores se ven.

Para exponer los servicios de web se definio otra network llamada frontnet.

