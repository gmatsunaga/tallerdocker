# Ejercicio 05

A continuacion se detalle para que sirven cada uno de estos comandos:

* HEALTHCHECK
* ONBUILD
* VOLUME

## HEALTHCHECK
Es una instruccion que se utiliza para indicarle al contenedor como comprobar que el contenedor esta funcionando correctamente. 
El comando o tarea de comprobacion debera retornar un valor numerico:

    0: success - the container is healthy and ready for use
    1: unhealthy - the container is not working correctly

Ejemplo Para un Web server, una tarea de healthcheck podria ser crear un peticion de prueba al web server cada cierto intervalo de tiempo:
    HEALTHCHECK --interval=5m --timeout=3s \
    CMD curl -f http://localhost/ || exit 1

## ONBUILD
Es una instruccion que se utiliza para disparar otro comando cuando la imagen es tomada de base para buildear otra imagen. Podria pensarse como que es un POST EVENTO de la imagen base.

Asi como el RUN permite ejectutar comandos al momento de buildear una imagen, ya una vez creada es e RUN no corre mal, sin embargo el ONBUILD correra en el futuro toda vez que alguna imagen que la extienda se builde.

Por ejemplo, podria ser copiar el contenido de Codigo en el folder donde raiz desde donde se llama, a la carperta /app/src
    [...]
    ONBUILD ADD . /app/src
    ONBUILD RUN /usr/local/bin/python-build --dir /app/src
    [...]

En La directiva ONBUILD estan excluidos los comandos: FROM o MAINTAINER

## VOLUME
Crea un punto de montaje dentro del contenedor y lo expone como un "volumen" de Docker. 

Se puede decir que este comando permite exportar como volumen una carpeta dentro del contenedor, algo que podria ser necesario en casos cuando esos datos son un paso previo de construccion de otro contenedor.




