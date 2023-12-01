# Guia de instalación y despliegue

Owner: Amador Sabido Carrero

## 1. Creación de la Base de Datos en CDmon
En primer lugar es necesario crear una Base de Datos que alojará toda la información de la aplicación.  
Nombre de la Base de Datos: **alimentos22023**

### 1.1. Creación de la tabla Alimentos
Para el correcto funcionamiento de la aplicación se requiere que exista una tabla Alimentos. Basta con ejecutar el siguiente script SQL:

```
CREATE TABLE `alimentos` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `nombre` varchar(255) NOT NULL,
  `energia` decimal(10,0) NOT NULL,
  `proteina` decimal(10,0) NOT NULL,
  `hidratocarbono` decimal(10,0) NOT NULL,
  `fibra` decimal(10,0) NOT NULL,
  `grasatotal` decimal(10,0) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB  DEFAULT CHARSET=utf8;
```
## 2. Despliegue de la aplicación en CDmon
### 2.1. Mediante GitHub + SSH
Mediante este método se clona el repositorio directamente desde GitHub en el Hosting compartido. Para ello nos conectamos a traves de SSH.
La secuencia de comandos necesarios es la siguiente:

```
ssh amadorsa93@134.0.11.19 
```
Si la conexión es exitosa nos pedirá la contraseña y ya estaremos dentro del Hosting.
La ruta por defecto cuando accedemos es **/entrada**. Debemos salirnos de esta carpeta y acceder a **/web**, que es a carpeta visible de nuestro Hosting compartido. Para ello:

```
cd ../web
```
Creamos una carpeta que contendrá todos los archivos de la aplicación

```
mkdir practica 
cd practica/
```
Una vez en la carpeta, clonamos el repositorio de GitHub. Pero antes es necesario deshabilitar la verificación SSL para las conexiones HTTPS en Git a nivel global. Esto hará que Git deje de verificar la autenticidad del certificado SSL al conectarse a servidores remotos a través de HTTPS. De lo contrario no podremos clonar nuetro repositorio en el Hosting.
```
git config --global sslVerify false
```
Finalmente clonamos el repositorio

```
git clone https://github.com/RpuecarCamas/GRUPO2DAW23.git .
```

Tras esto ya tendremos la aplicación disponible a través de la URL:  
http://amadorsabido.com.mialias.net/practica/web/

### 2.2 Subida de archivos mediante FTP

Si no podemos conectarnos mediante SSH este es el método alternativo: subir los archivos manualmente mediante el gestor web FTP que ofrece CDmon.
Una vez subido el **.zip** con los archivos de la aplicación basta con descomprimirlo y la aplicación estaría disponible en la misma URL mencionada anteriormente.

