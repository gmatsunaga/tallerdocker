
# Ejercicio 08
  

## Consideraciones

Para resolver el ejercicio se plantea utilizar 1 instancia de nginx como load balancer que apunte a los upstream web1 y web2, dos instancias de passwordapi

  

								WEB1
								/
	NGINX => Proxy Pass UPSTREAM
								\
								WEB2

  
Para esto utilizaremos la configuracion del archivo site.conf

## Para iniciarlo

Para esto se ejecuta el siguiente comando:

 docker-compose up

## Haciendo pruebas

Para revisar como levanto el compose ejecutamos:

	docker ps

y podemos identificar los id de contenedor ea99ca8025f8 y 3a52061ec551 para los contenedores web1 y web2

CONTAINER ID   IMAGE                         COMMAND                  CREATED         STATUS          PORTS                            NAMES
b5b7a9f60585   nginx:1.13                    "nginx -g 'daemon of…"   2 minutes ago   Up 39 seconds   80/tcp, 0.0.0.0:3000->3000/tcp   ejercicio08_balanceador_1
ea99ca8025f8   nicopaez/password-api:2.1.0   "docker-entrypoint.s…"   2 minutes ago   Up 40 seconds   3000/tcp                         ejercicio08_web2_1
3a52061ec551   nicopaez/password-api:2.1.0   "docker-entrypoint.s…"   2 minutes ago   Up 40 seconds   3000/tcp                         ejercicio08_web1_1

Para verificar el balanceo ejecutamos varios request con CURL:

	curl --location --request GET 'http://127.0.0.1:3000/health'

y obtuvimos las siguientes respuestas:

Respuesta 1:

	{
		"host": "ea99ca8025f8",
		"loadavg": [
			0.30322265625,
			0.15576171875,
			0.26953125
		],
		"freemem": 10403590144,
		"appversion": "2.1.0"
	}

Respuesta 2:

	{
		"host": "3a52061ec551",
		"loadavg": [
			0.2353515625,
			0.14697265625,
			0.26513671875
		],
		"freemem": 10402557952,
		"appversion": "2.1.0"
	}

donde identificamos como nombre de host a los container id antes mencionados, por lo que podemos verificar que esta balanceando entre ambas instancias.