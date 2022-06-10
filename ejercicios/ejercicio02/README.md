# Ejercicio 02

## Descarga de imagen original y push de imagen a repo propio

```
docker login
docker pull nicopaez/pingapp:3.0.0
docker tag nicopaez/pingapp:3.0.0 ifurey/ejercicio2:1.0.0
docker push ifurey/ejercicio2:1.0.0
```

## Descarga nueva imagen

```
docker pull ifurey/ejercicio2:1.0.0
```