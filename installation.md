# MANUAL DE INSTALACIÓN DE OWNCLOUD DESDE UNA MAQUINA VIRTUAL DE UBUNTU DESDE ISARDVDI

Lo primero que tenemos que hacer ya cuando la maquina se a encendido y se ah ejecutado correctamente en la terminal hay que poner lo siguiente:

### 1. Tenemos que instalar los requisitos previos de PPA:

- sudo apt install software-properties-common -y

![cloud1](https://github.com/user-attachments/assets/2d21433d-bdba-4005-815b-876005de99f2)

### 2. Instalar las herramientas necesarias para poder trabajar con los paquetes personales de PPA

- LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y

![cloud2](https://github.com/user-attachments/assets/4a2eca2d-0176-4462-bdbf-b44d113d0820)

### 3. actualiza los repositorios

- sudo apt update

![cloud3](https://github.com/user-attachments/assets/b17b241a-a90b-4988-b3b2-5212a14a3c03)

### 4. Ahora en este paso procederemos a instalar las librerias de PHP de la version 7.4 con los siguientes comandos:

- sudo apt install php7.4 -y

- sudo apt install -y php libapache2-mod-php7.4

- sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl

![cloud4](https://github.com/user-attachments/assets/1aeb3e5f-b49d-4d05-b8bc-4568ce99c737)

![cloud5](https://github.com/user-attachments/assets/b2eb6bed-b970-4b5f-af79-97f8ee6ba94a)

![cloud6](https://github.com/user-attachments/assets/5894d1d3-af1f-463a-a250-27f4e0340de5)

### 5. Hemos de seleccionar la version de PHP que queramos

- sudo update-alternatives --config php

![cloud7](https://github.com/user-attachments/assets/a683e1e5-07ed-4364-bf85-0446661ce066)

### 6. Activamos los modulos del apache2 necessarios

- sudo a2enmod proxy_fcgi setenvif

- sudo a2enconf php7.4-fpm

### 7. Despues de poner estos comandos reiniciamos el apache2

sudo service apache2 restart

![cloud8](https://github.com/user-attachments/assets/1f991354-bdd8-4e31-9432-1f23627cf226)




# Instalación y configuración de aplicaciones web

Para instalar una aplicación web, hay que copiar su código fuente al directorio raíz del servidor, que en el caso de apache2 es /var/www/html. Una vez allí, será accesible desde http://localhost.

# Instalación del apache2, mysql y algunas librerias del contenedor

### 1. Para empezar tenemos que actualizar la maquina con los siguientes comandos

- sudo apt update

- sudo apt upgrade

![cloud9](https://github.com/user-attachments/assets/62f9e123-fc49-4d25-99f7-7dfc971e8334)

![cloud10](https://github.com/user-attachments/assets/b2de5ec3-1a96-4dd6-90b9-f9cb5b4b7567)

Y si cuando lo estamos actualizando nos sale de si queremos continuar de si o no le tenemos que dar a que si

![cloud11](https://github.com/user-attachments/assets/f6c1df7e-b48a-4b8a-bcd7-9632cb5d2167)


### 2. Ahora procedemos a instalar el servidor web apache2
- sudo apt install -y apache2

![cloud12](https://github.com/user-attachments/assets/15335bc5-bbe7-4021-a173-4ae620e46f25)

### 3. Instalamos el servidor de bases de datos que es mysql-server

- sudo apt install -y mysql-server

![cloud13](https://github.com/user-attachments/assets/2f1f4806-54d2-4da7-bcda-133cb6d4d918)

### 4. Instalación de las librerias de PHP que es el lenguaje principal que utilizan las aplicaciones

- sudo apt install -y php libapache2-mod-php

- sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl

![cloud14](https://github.com/user-attachments/assets/4cbb084b-928c-4d2b-be6a-695e25393236)

![cloud15](https://github.com/user-attachments/assets/ff2fa9cd-d8eb-4c2e-9318-4127c1336ec8)

### 5. Reiniciamos el servidor del apache2

- sudo systemctl restart apache2

![cloud16](https://github.com/user-attachments/assets/33080ca6-6085-4349-a2a0-66e2da08eb33)

# Configuración mysql 

### 1. Procedemos a acceder a la consola de mysql desde la terminal o desde donde estemos root tenemos que ejecutar la siguiente comanda

- sudo mysql

![cloud17](https://github.com/user-attachments/assets/95f154f7-2fb4-4180-92f7-a8c28de1483d)

### 2. Creación de la base de datos, cuando estemos dentro de la consola de mysql hemos de crear una comanda para crear la base de datos y vamos a utilizar el nombre de bbdd

- CREATE DATABASE bbdd;

![cloud17](https://github.com/user-attachments/assets/12f7c35e-b4cb-44d3-aae1-08dd735cead8)

### 3. Creación de un usuario hay que tener en cuenta que la IP desde la que se va acceder base de dades es localhost

- CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

![cloud17](https://github.com/user-attachments/assets/0aef388b-5515-44d7-be10-959a859ceaa9)


### 4. En este paso vamos a dar privilegios al usuario con la siguiente comanda

- GRANT ALL ON bbdd.* to 'usuario'@'localhost';

![cloud17](https://github.com/user-attachments/assets/e1f7e0d2-3f8f-4bff-85da-ae0b4ebc687c)

### 5. Para salir de la base de datos hay que escribir lo siguiente

- exit

![cloud17](https://github.com/user-attachments/assets/829d0feb-070c-4b4d-a22e-0dc1832ad397)

### 6. Y por ultimo probamos la conexión a la base de datos pero para eso hemos de ir a una terminal con un usuario sin privilegios y ponemos lo siguiente

- mysql -u usuario -p


# Descargar el fichero de la aplicación web 

### 1. Vamos al directorio /var/www/html y descomprime allí el archivo de la aplicación web, debes sustituir app-web.zip por el nombre de tu archivo descargado con la aplicación web y el nombre de la carpeta app-web por la carpeta que se haya creado, si tu instalación de Linux está en otro idioma diferente al catalán y no tienes la carpeta Baixades, modifica el comando según tus necesidades.

- sudo cp ~/Baixades/app-web.zip /var/www/html

![cloud18](https://github.com/user-attachments/assets/e98cdf23-ae83-4401-a0e0-db9574a26b6b)

### 2. Procedemos a ir al directorio de /var/www/html

- cd /var/www/html

![cloud18](https://github.com/user-attachments/assets/a7e79b98-d399-4bce-a1bd-dd61af7175cd)

### 3. Ahora descomprimimos el fichero que hemos descargado

- sudo unzip app-web.zip

![cloud18](https://github.com/user-attachments/assets/66345beb-9472-4ddf-a15d-126cc0423d7d)

### 4. Copia los archivos en /var/www/html y sustituye app-web por el nombre de la carpeta descomprimida.

- sudo cp -R app-web/. /var/www/html

### 5. Eliminamos la carpeta creada cuando hemos hecho el unzip

- sudo rm -rf app-web/

![cloud19](https://github.com/user-attachments/assets/a960e5db-4a06-4677-84a8-2f374112c0fc)

### 6. Eliminamos el fichero de index.html de el apache2

- sudo rm -rf /var/www/html/index.html

![cloud20](https://github.com/user-attachments/assets/66d7c066-d25b-42aa-96a0-4c90e007dcfb)


# Aplicación de permisos a nuestra aplicación web

### Cuando hemos descomprimido el fichero de la aplicación web al directorio /var/www/html, aplicamos los siguientes permisos al directorio /var/www/html, tienes que seguir estos pasos para poder hacerlo

### 1. cd /var/www/html

### 2. sudo chmod -R 775 .

### 3. sudo chown -R usuario:www-data .

![cloud21](https://github.com/user-attachments/assets/5c48e0db-c106-414e-93c0-ff5e02f51396)



# Probamos a acceder a nuestro navegador para ver como funciona todo

Abre el navegador web y escribe la dirección http://localhost para configurar la nube.

Si todo ha salido bien y has seguido el manual, aparecerá el instalador de la aplicación web que descargaste. Te pedirá que crees un usuario administrador y que introduzcas la información de la base de datos.

Los datos que debes ingresar (si no has cambiado nada del manual) son:

- Usuario: usuario

- Contraseña: password

- Base de datos: bbdd

- Dominio: localhost






