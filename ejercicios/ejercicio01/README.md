# Ejercicio 01
## Runnning options
### Run with bind mount volume
```
$ cd .../ejercicios
$ docker run -it --rm -d -p 8080:80 --name bestpageever -v ejercicio01:/usr/share/nginx/html nginx:1.22
```
### Build image and run
```
$ cd .../ejercicios/ejercicio01
$ docker build -t ejercicio01 .
$ docker run -it --rm -d -p 8080:80 --name bestpageever ejercicio01
```