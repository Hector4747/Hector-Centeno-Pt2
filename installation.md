# MANUAL DE INSTALACIÓN DE OWNCLOUD DESDE UNA MAQUNA VIRTUAL DE UBUNTU DESDE ISARDVDI

Lo primero que tenemos que hacer ya cuando la maquina se ah encendido y se ah ejecutado correctamente en la terminal hay que poner lo siguiente:

### 1. Tenemos que instalar los requisitos previos de PPA:

sudo apt install software-properties-common -y

![cloud1](https://github.com/user-attachments/assets/2d21433d-bdba-4005-815b-876005de99f2)

### 2. Instalar las herramientas necesarias para poder trabajar con los paquetes personales de PPA

LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y

![cloud2](https://github.com/user-attachments/assets/4a2eca2d-0176-4462-bdbf-b44d113d0820)

### 3. actualiza los repositorios

sudo apt update

![cloud3](https://github.com/user-attachments/assets/b17b241a-a90b-4988-b3b2-5212a14a3c03)

### 4. Ahora en este paso procederemos a instalar las librerias de PHP de la version 7.4 con los siguientes comandos:

sudo apt install php7.4 -y

sudo apt install -y php libapache2-mod-php7.4

sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl

![cloud4](https://github.com/user-attachments/assets/1aeb3e5f-b49d-4d05-b8bc-4568ce99c737)

![cloud5](https://github.com/user-attachments/assets/b2eb6bed-b970-4b5f-af79-97f8ee6ba94a)

![cloud6](https://github.com/user-attachments/assets/5894d1d3-af1f-463a-a250-27f4e0340de5)

### 5. Hemos de seleccionar la version de PHP que queramos

sudo update-alternatives --config php

![cloud7](https://github.com/user-attachments/assets/a683e1e5-07ed-4364-bf85-0446661ce066)

### 6. Activamos los modulos del apache2 necessarios

