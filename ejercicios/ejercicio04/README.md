# Ejercicio 04

Link a la imagen creada [ifurey/ejercicio04](https://hub.docker.com/repository/docker/ifurey/ejercicio04)

## Build image

```
docker build -tag ejercicio04 .../ejercicios/ejercicio04
```

## Run image

```
docker run -d -p 30000:8080 ifurey/ejercicio04:1
```

to test access [http://localhost:30000](http://localhost:30000)

## Imagen base

La imagen base elegida fue [openjdk:11](https://hub.docker.com/_/openjdk). Principalmente por ser una imagen oficial
con JDK simple.