# puede visualizarse en ejecución en

<a href="https://php-7-3.drvelasquezq.site/" target="_blank">https://php-7-3.drvelasquezq.site/</a>

<a href="https://php-7-3.drvelasquezq.site/test.php" target="_blank">https://php-7-3.drvelasquezq.site/test.php</a>

<a href="https://php-7-3.drvelasquezq.site/xdebug.php" target="_blank">https://php-7-3.drvelasquezq.site/xdebug.php</a>

## Descripción

Este proyecto da los pasos para utilizar y crear imagen de docker que ejecuta una aplicación de PHP integrando Apache en Debian

<ul>
<li>Apache: 2.4.62</li>
<li>PHP: 7.3</li>
<li>Debian: Bookworm</li>
</ul>

## Docker hub

[https://hub.docker.com/r/drvelasquezq/php-7.3-apache2-bookworm](https://hub.docker.com/r/drvelasquezq/php-7.3-apache2-bookworm)

## caracteristicas

<ul>
<li>Permite depurar el código con VS Code con Xdebug 3.2.0 con Docker</li>
</ul>

# Uso

```bash
# clonar proyecto
git clone https://github.com/drvelasquezq/docker-php-7.3-apache2-bookworm.git
# ingresar al proyecto
cd docker-php-7.3-apache2-bookworm
# crear contenedor
docker compose up -d
```

luego podrá ingresar a: 
<br>
http://localhost:8050
<br>
http://localhost:8050/test.php
<br>
http://localhost:8050/xdebug.php

### ejemplo para construir la imagen: 
```bash
docker build --no-cache --progress=plain --tag drvelasquezq/php-7.3-apache2-bookworm:latest . > output-build-image/output.log 2>&1
```

### ejemplo para crear contenedor que solo ejecute el script sh que ya está en la imagen
```bash
docker run --name container-php-7.3-apache2-bookworm drvelasquezq/php-7.3-apache2-bookworm:latest
```

### ejemplo para crear contenedor con la imagen y ejecutarlo de manera interactiva:
```bash
docker run --tty --interactive -p 8050:80 --name container-php-7.3-apache2-bookworm drvelasquezq/php-7.3-apache2-bookworm:latest bash
```

### ejemplo para crear contenedor con la imagen y ejecutarlo en segundo plano
```bash
docker run -d -p 8050:80 --name container-php-7.3-apache2-bookworm ||drvelasquezq/php-7.3-apache2-bookworm:latest
```
```bash
# para luego ingresar al contenedor
docker exec -ti container-php-7.3-apache2-bookworm bash
```

### ejemplo para remover contenedor:
```bash
docker rm -f container-php-7.3-apache2-bookworm
```

### ejemplo de copia de archivo:
```
docker cp container-php-7.3-apache2-bookworm:/etc/php/7.3/cli/php.ini ./etc/php/7.3/cli/
```

### ejemplo para subir imagen a docker hub
```bash
docker tag drvelasquezq/php-7.3-apache2-bookworm:latest usuario/php-7.3-apache2-bookworm:latest
```
```
docker push drvelasquezq/php-7.3-apache2-bookworm:latest
```