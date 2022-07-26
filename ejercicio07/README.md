# Ejercicio 07

## ¿Cuántos contenedores se están ejecutando?
Segun docker-compose-jobvacancy.yml son 2 (dos) contenedores, uno llamado **web** y otro llamado **db**

    services:
    
    web: ...
    
    db: ...

Ejecutando docker ps, son 2 (dos) contenedores uno con imagen 'nicopaez/jobvacancy-ruby:1.3.0' y otro con imagen 'postgres:14.4-alpine'

    CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
    
    84ed5d4da161 nicopaez/jobvacancy-ruby:1.3.0 "/jobvacancy/start_a…" 13 seconds ago Up 12 seconds 0.0.0.0:3000->3000/tcp ejercicio07_web_1
    f76653096eeb postgres:14.4-alpine "docker-entrypoint.s…" About a minute ago Up 13 seconds 5432/tcp ejercicio07_db_1


## ¿Cuales son las imágenes en las que están basados los mencionados contenedores?

Segun docker-compose-jobvacancy.yml las imagenes son para web 'nicopaez/jobvacancy-ruby:1.3.0' y para db 'postgres:14.4-alpine'

    services:
	    web:
		    image: nicopaez/jobvacancy-ruby:1.3.0
		    ...
	    db:
		    image: postgres:14.4-alpine
		    ...

Lo mismo segun docker ps, se verifica que las imagenes son 'nicopaez/jobvacancy-ruby:1.3.0' y 'postgres:14.4-alpine'
 

    CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
    
    84ed5d4da161 nicopaez/jobvacancy-ruby:1.3.0 "/jobvacancy/start_a…" 13 seconds ago Up 12 seconds 0.0.0.0:3000->3000/tcp ejercicio07_web_1
    f76653096eeb postgres:14.4-alpine "docker-entrypoint.s…" About a minute ago Up 13 seconds 5432/tcp ejercicio07_db_1

  

## ¿Puedes leer el docker-compose-jobvacancy.yml y describir lo que hace cada una de sus lineas?

    services:
	    web:
		    image: nicopaez/jobvacancy-ruby:1.3.0 #Define la imagen del contenedor WEB
		    links:
			    - db # Define el alias db para que sea visible el contenedor DBd dentro de WEB
		    ports:
			    - "3000:3000" #Expone el puerto externo 3000 del interno 3000
		    environment:
			    PORT: "3000" #Define la variable de entorno PORT con el valor 3000
			    RACK_ENV: "production" Define la variable de entorno RACK_ENV con el valor production
			    DATABASE_URL: "postgres://postgres:Passw0rd!@db:5432/postgres" #Define el connection String de la Base de datos
		    depends_on:
			    - db # Marca como dependencia al servicio db para que primero incialice db luego caundo este READY incialice el servicio web
	    db:
			image: postgres:14.4-alpine #Define la imagen del contenedor DB
	    environment:
		    POSTGRES_PASSWORD: Passw0rd! #Define la variable de entorno POSTGRES_PASSWORD con el valor Passw0rd! para que se inicialice bien la imagen

  

## Dado que cada contenedor corre en forma aislada ¿Cómo es posible que esos contenedores se vean entre sí?

Cuando docker compose levanta los contenedores a partir de un docker compose file lo hace dentro de una misma network, tomando el nombre del directorio raiz, eso lo podemos ver con el siguiente comando:

    docker network ls

En mi caso particular la network creada es ejercicio07_default y vamos a inspeccionarla:

    docker network inspect ejercicio07_default

Hay podemos concluir que ambos contenedores "ejercicio07_web_1" y "ejercicio07_db_1" estan dentro de misma network, con IPS 172.21.0.3 y 172.21.0.2 respectivamente, segun se puede ver en analisis de docker network inspect. Adicionalmente con la directiva "link" en el docker compose se facilita la resolucion de host con IP para vincular los servicios de db dentro del contenedor web.

    [
	    {
		    "Name": "ejercicio07_default",
		    "Id": "0506c0f23b68133457ff80d242aa2e70608df25b08e12ed9f428247f0773ee3e",
		    "Created": "2022-07-26T16:59:50.6801081Z",
		    "Scope": "local",
		    "Driver": "bridge",
		    ...
		    "Containers": {
			    "84ed5d4da161466752e2914b46d07b0da0198c4c032ad8b333cbd7a3286e174e": {
			    "Name": "ejercicio07_web_1",
			    "EndpointID": "59665dfe8e184ec9ed8253cc13ce9ce209848e0786f7b8849cf485e13c284d0b",
			    "MacAddress": "02:42:ac:15:00:03",
			    "IPv4Address": "172.21.0.3/16",
			    "IPv6Address": ""
		    },
		    "f76653096eebb2289ad5e3fa9fc3b91310c083e242d796847f24157c23bc0cdc": {
			    "Name": "ejercicio07_db_1",
			    "EndpointID": "07d174f39bc0b6ff686763279f50854124073df60d35b0fe9f3bc5f6b771ae35",
			    "MacAddress": "02:42:ac:15:00:02",
			    "IPv4Address": "172.21.0.2/16",
			    "IPv6Address": ""
		    }
		    },
		    ...
	    }
    ]
