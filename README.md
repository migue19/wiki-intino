# Wiki Intino

Documentacion sobre Intino y uso de este framework.

## Requisitos de Instalación en Servidor

## Prerequisitos

Tener instalado Docker

## Pasos de Instalación

Clonar el repositorio:
```bash 
git clone https://github.com/migue19/wiki-intino.git
```

Dentro de la carpeta raiz del proyecto existe el archivo llamado `Dockerfile` el cual tenemos que ejecutar con el comando

```bash
docker build -t wiki .
```

con esto se creara la imagen de docker y para ejecutar el contenedor se corre el comando:

```bash
docker run -p 3001:3000 -d --restart unless-stopped wiki
```

## Pasos de Actualización

para ejecutar una actualizacion se debe actualizar el repositorio

```bash
git pull
```

Construir nuevamente la imagen de docker

```bash
docker build -t wiki .
```

Listar los contenedores activos

```bash
docker ps
```
Detener el contenedor

```bash
docker stop container-id
```

levantar el contenedor nuevamente

```bash
docker run -p 3001:3000 -d --restart unless-stopped wiki
```