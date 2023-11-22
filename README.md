# Arquitectura Hexagonal con Symfony 6

Vamos a generar un pequeño proyecto que tenga una API usando:

- Symfony 6
- Docker

Para lo cual lo primero que vamos a hacer es crear un archivo docker-compose.yml con el siguiente codigo:

***NOTA:*** _Asumimos que se tiene Docker o Docker Desktop instalado en el equipo_

**docker-compose.yml**
```yaml
version: '3.5'

services:
  installer:
    image: composer:latest
    volumes:
      - ./:/app
    working_dir: /app
    ports:
      - 8000:8000
```

Una vez que lo tenemos, ejecutamos el siguiente comando:

```shell
$ docker-compose run --rm --service-ports installer bash
```

Cuando ya nos encontremos dentro del contenedor, basandonos en la documentación oficial de Symfony (https://symfony.com) 
instalamos el CLI de Symfony (nos basamos en la instalacion para LINUX)

```shell
curl -sS https://get.symfony.com/cli/installer | bash
mv /root/.symfony5/bin/symfony /usr/local/bin/symfony
```

Ahora si, instalamos un nuevo proyecto de Symfony usando el CLI que acabamos de instalar.

***NOTA:*** Vamos a instalar la ultima versión de Symfony, pero sin **--webapp** ya que no necesitamos todas las dependencias, solo vamos a construir un API

```shell
symfony new library
```

