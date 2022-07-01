# Ejercicio 07

## ¿Cuántos contenedores se están ejecutando?
Dos contenedores:
* uno con imagen `nicopaez/jobvacancy-ruby:1.3.0`
* otro con imagen `postgres`

```
$ docker ps
CONTAINER ID   IMAGE                            COMMAND                  CREATED          STATUS          PORTS                                       NAMES
dc21d5725a48   nicopaez/jobvacancy-ruby:1.3.0   "/jobvacancy/start_a…"   18 minutes ago   Up 18 minutes   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp   ejercicio07-web-1
0df5d4009aad   postgres                         "docker-entrypoint.s…"   18 minutes ago   Up 18 minutes   5432/tcp 
```


## ¿Cuales son las imágenes en las que están basados los mencionados contenedores?
ya respondido arriba

## ¿Puedes leer el docker-compose-jobvacancy.yml y describir lo que hace cada una de sus lineas?
Going line by line




```
version: '2'
```
Docker compose version to be used

```
services: 
```
Lista de contenedores

```
  web: 
```
Definicion de service named `web`

```
    image: nicopaez/jobvacancy-ruby:1.3.0 
```
docker image to use in the service `web`

```
    links:

      - db
```
Cointainer relations
```
    ports: 
      - "3000:3000"
```
Mapping ports

```
    environment:
      PORT: "3000"
      RACK_ENV: "production"
      DATABASE_URL: "postgres://postgres:Passw0rd!@db:5432/postgres"
```
Defines envirnoment vars for service `web`

```
    depends_on:
      - db
```
Other services tag that `web` depends on


```
  db:
```
Definicion de service named `db`
```
    image: postgres
```
docker image to use in the service `db`
```
    environment:
      POSTGRES_PASSWORD: Passw0rd!
```
Defines envirnoment vars for service `db`

## Dado que cada contenedor corre en forma aislada ¿Cómo es posible que esos contenedores se vean entre sí?

la linea 5 y 6 del file docker-compose-jobvacancy.yml disponibilizan el servicio `db` para `web`

```
    links:
      - db
```
