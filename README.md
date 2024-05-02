# PHP_Doc

[//]: # (version: 2.0)
[//]: # (author: Fran Dona Villar)
[//]: # (date: 2024-01-23)


- [PHP\_Doc](#php_doc)
  - [¿Que es PHP?](#que-es-php)
  - [Instalación de PHP](#instalación-de-php)
  - [Estructura documentos PHP](#estructura-documentos-php)
    - [Incrustaciones](#incrustaciones)
    - [Archivos Únicos](#archivos-únicos)
    - [Vincular archivos PHP](#vincular-archivos-php)
    - [Contenido del Repositorio](#contenido-del-repositorio)
  - [Estructura del Repositorio (por carpetas)](#estructura-del-repositorio-por-carpetas)
    - [LOG ERRORES](#log-errores)
    - [LOGIN](#login)
      - [CREDENCIALES UNICAS](#credenciales-unicas)
      - [GRUPO DE CREDENCIALES](#grupo-de-credenciales)
    - [CONEXION BBDD](#conexion-bbdd)
    - [CRUD](#crud)
      - [CREATE](#create)
      - [DELETE](#delete)
      - [READ](#read)
      - [UPDATE](#update)

## ¿Que es PHP?
PHP es un lenguaje de programación web utilizado para crear sitios dinámicos y aplicaciones. Se ejecuta en el servidor y permite integrar código PHP con HTML para generar contenido personalizado. Su popularidad se debe a su facilidad de uso y a su gran comunidad de desarrolladores.

## Instalación de PHP

>[!NOTE]
Pruebas realizadas en Linux + Apache

```bash
sudo apt update
sudo apt -y install software-properties-common
sudo add-apt-repository ppa:ondrej/php
# Pulsamos ENTER

sudo apt update
sudo apt upgrade

sudo apt -y install php

# Revisamos la version
php -v

# Instalacion de depencencias mas usadas
sudo apt-get install php-pgsql
sudo apt-get install php-xsl
sudo apt-get install php-amqp
sudo apt-get install openssl
sudo apt-get install php-redis
```
<br>

>[!NOTE]
Pasos adicionales si usamos MongoDB

```bash
# Para instalar el Soporte MongoDB
# IMPORTANTE! Si no usamos MongoDB NO LO INSTALAES
sudo apt install php-dev php-pear
sudo pecl install mongodb
# Vemos el listado de librerias instaladas (incluidas las de arriba)
php -m

sudo nano /etc/php/8.2/cli/php.ini
# Dentro del archivo...
extension=mongodb.so
# CTRL + O (Guardar) y CTRL+X (salir)
sudo service apache2 restart
```
---- 

>[!NOTE]
Seguimos con la intalacion normal
```bash
# Instalamos CGI
sudo apt-get install php-cgi

sudo apt-get install php-fpm
# Hay que activar el FPM en el Apache
sudo a2enmod proxy_fcgi setenvif
sudo a2enconf php-fpm

sudo service apache2 restart


# Instalamos dependencias y nos lo bajamos
sudo apt update
sudo apt install curl php8.2-cli php8.2-mbstring git unzip

# Damos permisos al directorio de publicación
sudo chmod 777 -R /var/www/html 
```

## Estructura documentos PHP

### Incrustaciones

Podemos hacer incrustaciones de php en cualquier parte del documento según necesitemos.

```php
<?php
    echo "Podemos crear incrustaciones donde necesitemos usando <?php ?>";
?>
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Incrustaciones</title>
</head>
<body>
    <p>Hola Mundo!</p>
    <?php
    echo "De igual manera dentro del código, usando <?php ?>";
    ?>
</body>
</html>
```
[-> Enlace a Ejemplo <-](ejemplos/0.%20ESTRUCTURA/incrustaciones.php)

### Archivos Únicos

Estos archivos únicamente contienen contenido php, se utilizan para crear archivos de funciones concretas que se vinculan al archivo principal.
No es necesario usar la etiqueta de cierre **?>**

```php
<?php
    echo "Documento único php";

```
[-> Enlace a Ejemplo <-](ejemplos/0.%20ESTRUCTURA/archivo_unico.php)

### Vincular archivos PHP

Podemos usar diferentes tipos de vinculacion:

- **include**: Incluye un archivo. Si el archivo no se encuentra o hay un error, PHP solo emite una advertencia y continúa ejecutando el script.
  
- **require**: Similar a include pero si el archivo no se encuentra o hay un error, PHP emite un error fatal y detiene la ejecución del script.
  
-  **include_once**: Incluye el archivo solo una vez durante la ejecución del script, incluso si se llama varias veces.

-  **require_once**: Similar a include_once pero con el mismo comportamiento de require en caso de error.

```php
<?php 

include ('archivo.php');

require ('archivo.php');

include_once ('archivo.php');

require_once ('archivo.php');
?>

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Vinculacion de Archivos</title>
</head>
<body>
    <p>Hola Mundo!</p>
</body>
</html>
```
[-> Enlace a Ejemplo <-](ejemplos/0.%20ESTRUCTURA/vincular_archivos.php)



### Contenido del Repositorio

- Repositorio para estructuras de php y archivos copy paste
---------


## Estructura del Repositorio (por carpetas)

### LOG ERRORES
- 📄**errores.php:** Archivo para mostrar errores en pantalla, también generara un segundo archivo .log de esta manera será mas fácil detectar errores.
---


### LOGIN

#### CREDENCIALES UNICAS
- 📄**login.php:** Login sencillo con unas credenciales ya establecidas
  
#### GRUPO DE CREDENCIALES
- 📄**BBDD_login.php:** Login con unas credenciales establecidas en una base de datos externa
----


### CONEXION BBDD
 Conexión y verificación de la BBDD

- 📄**conexionbbdd.php:** Contiene el código para una conexión y verificación sin archivo externo
- 📄**FUNCION_conexionbbdd.php:** Contiene el código para crear la conexión y verificación desde un archivo de funciones externo
----


### CRUD

#### CREATE
- 📄**create.php:** Creación de Create sin archivo externo
- 📄**FUNCION_create.php:** Creación de Create con archivo externo
  
#### DELETE
- 📄**delete_fisico_logico.php:** Archivo con tabla para usar la función lógica y física
- 📄**funciones_delete:** Archivo de funciones para usar las funciones delete lógico y físico

#### READ
- 📄**read.php:** Estructura para visualizar los datos en una tabla, con nombres personalizados

#### UPDATE
- 

---
