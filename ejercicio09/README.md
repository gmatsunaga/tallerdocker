# Ejercicio 09

## Manejo de Secrets con Docker Compose v2
Como Docker Compose v2 no soporta secrets, recien disponible a partir de v3, la forma trabajar los secrets es definir archivos para almacenar las variables de entorno key/values

Para eso se definio el archivo db_pass.env para que el contenedor de db levante la variable de POSTGRES_PASSWORD necesaria para levantar postgres

Para eso se definio el archivo conn_str.env para que el contenedor de web se pueda conectar a la base de datos con la variable de DATABASE_URL

## Definicion de Networks
Para comunicar el servicio web y db se especifico una network llamada backnet, en la cual ambos contenedores se ven.

Para exponer los servicios de web se definio otra network llamada frontnet.

