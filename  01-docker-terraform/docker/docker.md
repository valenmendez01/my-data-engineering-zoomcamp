# Docker

## Qué es Docker

Docker es un software que permite ejecutar aplicaciones y su entorno de forma aislada en contenedores, de forma similar a una máquina virtual, pero mucho más liviano y rápido.

En lugar de instalar programas directamente en tu sistema operativo, Docker ejecuta las aplicaciones dentro de contenedores que incluyen todo lo necesario para que funcionen (igual que en cualquier servidor).

Ventajas:
* Reproducibilidad: El mismo entorno funciona en cualquier máquina.
* Aislamiento: Las aplicaciones no interfieren entre sí.
* Portabilidad: Funciona en local, servidores o nube.

## Conceptos principales

* Imagen (Image): Es una plantilla que contiene todo lo necesario para ejecutar un programa.

* Contenedor (Container): Es una instancia de una imagen en ejecución.

* Volumen (Volume): Los contenedores no guardan cambios por defecto, cada contenedor inicia desde la imagen original. Un volumen conecta una carpeta real de tu computadora con una carpeta del contenedor.

* Dockerfile: define cómo construir una imagen.

* Docker Compose: archivo que permite ejecutar múltiples contenedores con un solo comando.

### Comandos principales

Ver versión
```bash
docker --version
```

---
Descargar una imagen
```bash
docker pull ubuntu
```
Ver imágenes
```bash
docker images
```
Eliminar imagen
```bash
docker rmi image_name
```

---
Ejecutar contenedor interactivo (-i interactivo y -t terminal) a partir de una imagen
```bash
docker run -it ubuntu
```
Ver contenedores activos
```bash
docker ps
```
Ver todos los contenedores
```bash
docker ps -a
```
Eliminar contenedor
```bash
docker rm container_id
```

---
Montar volumen
```bash
docker run -v $(pwd)/data:/app/data ubuntu
```
* Crea y ejecuta un contenedor a partir de la imagen ubuntu
* -v significa volume mount. Conecta una carpeta de tu computadora con una carpeta dentro del contenedor.
* Formato general:
```bash
HOST_PATH : CONTAINER_PATH
```
Entonces carpeta de mi computadora ($(pwd)/data) : carpeta dentro del contenedor (/app/data)

---
Iniciar servicios Docker Compose
```bash
docker compose up
```
Detener servicios Docker Compose
```bash
docker compose down
```
Ver contenedores Docker Compose
```bash
docker compose ps
```

### Flujo

Cuando ejecutas docker compose up, Docker Compose hace lo siguiente:
* 1 Lee docker-compose.yml
* 2 Identifica los servicios
* 3 Para cada servicio:
  ** usa una imagen existente
  ** o construye una imagen desde un Dockerfile
* 4 Crea contenedores a partir de esas imágenes
* 5 Configura red, puertos y volúmenes
* 6 Inicia los contenedores

