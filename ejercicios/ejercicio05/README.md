# Ejercicio 05

## HEALTHCHECK
Define como testear un contenedor para determinar el status

### Usage:

`HEALTHCHECK [<options>] CMD <command>` (check container health by running a command inside the container)
`HEALTHCHECK NONE` (disable any healthcheck inherited from the base image)

### Information:

Tells Docker how to test a container to check that it is still working
Whenever a health check passes, it becomes healthy. After a certain number of consecutive failures, it becomes unhealthy.
The <options> that can appear are...
--interval=<duration> (default: 30s)
--timeout=<duration> (default: 30s)
--retries=<number> (default: 3)
The health check will first run interval seconds after the container is started, and then again interval seconds after each previous check completes. If a single run of the check takes longer than timeout seconds then the check is considered to have failed. It takes retries consecutive failures of the health check for the container to be considered unhealthy.
There can only be one HEALTHCHECK instruction in a Dockerfile. If you list more than one then only the last HEALTHCHECK will take effect.
<command> can be either a shell command or an exec JSON array.
The command's exit status indicates the health status of the container.
0: success - the container is healthy and ready for use
1: unhealthy - the container is not working correctly
2: reserved - do not use this exit code
The first 4096 bytes of stdout and stderr from the <command> are stored and can be queried with docker inspect.
When the health status of a container changes, a health_status event is generated with the new status.

## ONBUILD
  Agrega a la imagen una instruccion para que se triggerea posteriormente cuando la imagen es usada como base.

### Usage:

`ONBUILD <Dockerfile INSTRUCTION>`

### Information:

Adds to the image a trigger instruction to be executed at a later time, when the image is used as the base for another build. The trigger will be executed in the context of the downstream build, as if it had been inserted immediately after the FROM instruction in the downstream Dockerfile.
Any build instruction can be registered as a trigger.
Triggers are inherited by the "child" build only. In other words, they are not inherited by "grand-children" builds.
The ONBUILD instruction may not trigger FROM, MAINTAINER, or ONBUILD instructions.

## VOLUME
  Crea un mounting point como volumen externo

### Usage:

`VOLUME ["<path>", ...]`
`VOLUME <path> [<path> ...]`
