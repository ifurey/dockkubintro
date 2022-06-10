# Ejercicio 03
# Analisis de layers
Utilizando el comando `docker inspect NAME:TAG` se oberva:

- `nicopaez/passwordapi-java:java8-alpine` tiene en total 4 layers
- `nicopaez/passwordapi-java:java8-fabric` tiene en total 9 layers
- Comparten unicamente la primer layer id: `8e3ba11ec2a2` (`sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c`)


## A modo de comentario
Con el analisis previo en mente y considerando que el objetivo de las layers es evitar redundancia de datos reutilizando layers compartidas fui a ver los logs de las descargas de cada imagen.



#### Descarga de nicopaez/passwordapi-java:java8-alpine
```
$ docker pull nicopaez/passwordapi-java:java8-alpine
java8-alpine: Pulling from nicopaez/passwordapi-java
8e3ba11ec2a2: Pull complete 
311ad0da4533: Pull complete 
391a6a6b3651: Pull complete 
cc2824e94232: Pull complete 
Digest: sha256:58124e67b934e5f6adf2c3d528296e79705241291011ea5762ee6633d6184ab1
Status: Downloaded newer image for nicopaez/passwordapi-java:java8-alpine
docker.io/nicopaez/passwordapi-java:java8-alpine
```

#### Descarga de nicopaez/passwordapi-java:java8-fabric
```
$ docker pull nicopaez/passwordapi-java:java8-fabric
java8-fabric: Pulling from nicopaez/passwordapi-java
8e3ba11ec2a2: Already exists 
badf8d054232: Pull complete 
d7d4b67fcf69: Pull complete 
3ed763dda7b4: Pull complete 
1bb0a6746cf8: Pull complete 
3454c3be30cf: Pull complete 
369c59cc4ad1: Pull complete 
fc3c80fa4974: Pull complete 
9f7c344fecb0: Pull complete 
Digest: sha256:5aa4a6be9ec512ed350d850d4d328590ced48ae2845103deca8d3db5b3789d95
Status: Downloaded newer image for nicopaez/passwordapi-java:java8-fabric
docker.io/nicopaez/passwordapi-java:java8-fabric
```

En la descarga de `nicopaez/passwordapi-java:java8-alpine` se ven las descargas individuales de las 4 layers. Todas con el mensage `Pull complete`

En la descarga de `nicopaez/passwordapi-java:java8-fabric` se ven las descargas individuales de las 9 layers. La primera con el mensage `Already exists` puesto que al ser compartida con la descarga previa no es necesario descargarla. El resto con el mensage `Pull complete`.
