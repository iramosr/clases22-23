---
 DeApWeb - Despliegue de Aplicaciones Web
---

# T5 Introducción a Docker

Duración: 5 horas.
Fecha de examen: **25 oct**

## Play with docker
+ Docker CLI: En nativo (base GNU/Linux). Será lo que utilicemos.
+ Docker Desktop: Capa de virtualización intermedia (base Windows).
+ [Play with docker](https://labs.play-with-docker.com/): PAAS para aprender Docker sobre web.
+ Docker CLI sobre WSL (Windows subsystem for Linux): *no recomendado por Docker Inc.*
+ Docker CLI sobre VM (vagrant).

### Docker Desktop sobre WSL
*Incluída la versión HOME del sistema.*

1. [Instalar WSL2](https://www.docker.com/blog/docker-desktop-for-windows-home-is-here/)
2. [Config WSL2](https://learn.microsoft.com/en-us/windows/wsl/wsl-config)
   En */etc/wsl.conf*:
   ```
   [network]
   hostname = WSL-NOMBRE_DEL_HOST
   #generateHosts = false
   ```
   En */etc/hosts* añadir el NOMBRE_DEL_HOST:
   ```
   127.0.0.1   WSL-NOMBRE_DEL_HOST.local   WSL-NOMBRE_DEL_HOST
   ```
3. [WSL2 modo BRIDGE](https://develmonk.com/2021/06/05/easiest-wsl2-bridge-network-without-hyper-v-virtual-network-manager/)
3. b. [WSL2 modo BRIDGE con interfaz virtual](https://randombytes.substack.com/p/bridged-networking-under-wsl). *Puede hacerse con otros sistemas de virtualización además de Hyper-V.

## DOCKER sobre VPS
Como ya comentamos en clase, el desarrollo completo vamos a realizarlo fundamentalmente sobre VPS proporcionando las siguientes opciones al alumnado:
1. VPS **GRATUITOS**:
  1. [Oracle Cloud](https://signup.cloud.oracle.com/?sourceType=_ref_coc-asset-opcSignIn&language=en_ES?redirect_uri=https://cloud.oracle.com/) - requiere tarjeta de crédito.
  2. [GigaRocket](https://www.gigarocket.net/free-vps.php) - requiere participación activa (15 post) en los foros.
  3. [Kamatera](https://www.kamatera.com/express/compute/?HT=1&tcampaign=35426_385080_ha4134547238662234&bta=35426&nci=5566&afp=ha4134547238662234) - no requiere nada - 30 días sólo.
  4. [Digital Ocean](https://cloud.digitalocean.com/registrations/new) - 200$ de saldo gratis (válido para 2 meses).
2. VPS *LOW-COST* [VPS a 1€/mes](https://www.piensasolutions.com/vps)
3. Algunas opciones extra:
  1. [Servidores gratuitos](https://github.com/cloudcommunity/Free-Hosting?ref=reactivisima.com)
  2. [DeployHQ](https://www.deployhq.com/)


## Tutorial
[Tutorial](https://moodle.educarex.es/iescastelarfp/pluginfile.php/46278/mod_resource/content/1/contenedores.pdf)


## Práctica
Deberéis crear un conjunto de microservicios (con docker) compuesto por 3 contenedores:
+ Red interna para la comunicación entre contenedores
+ Microservicio `mariaDB` no accesible desde el mundo, sólo desde la red interna. Éste debe inicializarse con la creación del usuario `pepe`y el pass `despliegue`.
+ Microservicio `php-apache` que pueda acceder a la bbdd y desde el exterior en el puerto 80. Debe contener un `phpinfo()` en el archivo `info.php` de la raíz púbilica.
+ Microservicio `phpMyAdmin`que pueda accedar a la bbdd y sea accesible desde el exterior en el puerto 8080 o 443 si lo realizas desde un VPS. \
*Nota: para simplificar esta última conexión deberéis pasarle la variable de entorno `PMA_HOST=nombre_contenedor_mariaDB`.


*Nota: El sistema debe ser accesible por cualquiera desde internet (VPS) o ser facilitado en un entorno reproducible (vagrant) con instrucciones claras para su ejecución.*

> Fecha de entrega: **25 de octubre.**
> Forma de entrega: Subir como README.md a repositorio privado en una carpeta T5-Docker.
