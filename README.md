# Bieel-Manjon.pt2
# Instal·lació d'OwnCloud

## Instal·lació de la versió 7.4 de PHP a Ubnutu 24.04

Per a instal·lar OwnCloud necessitem la versió 7.4 de PHP.

Les comandes següents són les necessàries per a actualitzar el PHP.

Amb aquesta comanda instal·lem els requisits de PPA (arxius de paquets personals).

```bash

sudo apt install software-properties-common -y

```

Instal·lem les eines necessàries per a poder treballar amb PPA.

```bash

LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y

```

Actualitzem

``` bash

sudo apt update

```

Amb aquestes 3 comandes instal·lem les llibreries de PHP de la versió 7.4.

``` bash

sudo apt install php7.4 -y

```

``` bash

sudo apt install -y php libapache2-mod-php7.4

```

``` bash

sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl

```

Amb aquesta comanda seleccionem la versió de PHP que necessitem, en aquest cas necessitem la 7.4.

``` bash

sudo update-alternatives --config phpmmm

```

Ara activem els mòduls que necessitem d'Apache2 perquè funcioni.

``` bash

sudo a2enmod proxy_fcgi setenvif

```

``` bash

sudo a2enconf php7.4-fpm

```

Y per finalitzar amb l'instal·lació de la versió 7.4 de PHP, reiniciem l'Apache2.

``` bash

sudo service apache2 restart

```

## Comandes per l'instal·lació i configuració de OwnCloud

Per a instal·lar i configurar OwnCloud, farem ús d'apache2, al instal·lar Apache2 es crearà una carpeta dins de /var/www/html, on treballarem.

## Comandes per l'instal·lació d'Apache2 i mysql, i llibreries de PHP

Actualitzem la nostra màquina.

``` bash

sudo apt update

```

Aquesta no és obligatòria posar-la, però és millor, a més que triga molt en processar aquesta comanda.

``` bash

sudo apt upgrade

```

Instal·lem el servidor web d'Apache2

``` bash

sudo apt install -y apache2

```

Instal·lem la base de dades de mysql

``` bash

sudo apt install -y apache2

```

Instal·lem algunes llibreries PHP, que aquest és el llenguatge de totes les aplicacions.

``` bash

sudo apt install -y php libapache2-mod-php

```

``` bash

sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl

```

I per finalitzar reiniciem el servidor d'Apache2

``` bash

sudo systemctl restart apache2

```

## Configurem la base de dades de mysql

### Entrem a la consola de dades de mysql per posar totes aquestes comandes.

Des d'un terminal on siguem root posem aquesta comanda per entrar a la terminal de mysql

``` bash

sudo mysql

```
![Captura desde 2024-11-07 14-06-07(1)](https://github.com/user-attachments/assets/a0477b29-fd8f-4859-8ee9-8aabf9b613f3)

### Creem una base de dades.

Dins el terminal de mysql creem una base de dades, ja que a l'estar creant aquesta nova base de dades, li posem el nom de bbdd

``` bash

CREATE DATABASE bbdd;

```
![Captura desde 2024-11-07 14-06-20](https://github.com/user-attachments/assets/ab8def8a-e326-4a43-b230-16809fb4167f)

### Creació del nostre usuari

Ara hem de crear un nou usuari, amb un usuari i una contrasenya, a més que utilitzarem la IP de localhost

``` bash

CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

```
![Captura desde 2024-11-07 14-06-57](https://github.com/user-attachments/assets/d1611068-eeaf-4d1d-b109-e6531834f477)

### Per finalitzar li donem privilegis al nostre usuari

``` bash

GRANT ALL ON bbdd.* to 'usuario'@'localhost';

```
![Captura desde 2024-11-07 14-07-08](https://github.com/user-attachments/assets/e0b44991-d29e-46e2-a0d7-18a94b98d391)

### Sortim de la base de dades

``` bash

exit

```

### Ens assegurem que hem fet tots els passos bé.

Amb el terminal normal sense privilegis provem a connectar-nos a mysql i introduïm la nostra contrasenya de mysql.

``` bash

mysql -u usuario -p

```

## Descarreguem l'aplicació web

Descarreguem el .zip de la nostra cloud, en aquest cas la de OwnCloud:

https://download.owncloud.com/server/stable/owncloud-complete-20240724.zip

Ara copiem el .zip i ho peguem al directori /var/www/html per fer tot el que ens falta per fer (Baixades pot variar depenent de l'idioma que tinguis).

``` bash

sudo cp ~/Baixades/owncloud-complete-20240724.zip /var/www/html

```

Ara anem al directori /var/www/html

``` bash

cd /var/www/html

```

En aquest directori descomprimim el .zip que hem baixat.

``` bash

sudo unzip owncloud-complete-20240724.zip

```

Copiem els fitxers a la carpeta /var/www/html, i canviem els signes d'interrogant (??) pel nom del directori on s'ha descomprimit l'arxiu d'abans.

``` bash

sudo cp -R ??/. /var/www/html

```

Ara la carpeta creada de quan hem descomprimit l'arxiu, l'eliminem (tornem a cambiar ??, per el nom de la carpeta).

``` bash

sudo rm -rf ??/

```

Y per ultim eliminem el fitxer index.html de l'Apache2

``` bash

sudo rm -rf /var/www/html/index.html

```

## Permisos a les nostres aplicacions web.

Al tenir descomprimit el fitxer a /var/www/html donem permisos a aquest mateix directori amb les següents comandes.

``` bash

cd /var/www/html

```

``` bash

sudo chmod -R 775 .

```

``` bash

sudo chown -R usuario:www-data .

```

## Veure si podem accedir al navegador.

Entreu a http://localhost en el teu navegador web, i configura la teva Cloud.

Si heu fet bé tots els passos, us ficarà al OwnCloud, i us demanarà crear-vos un usuari d'admin i la base de dades que has configurat.

La teva informació seria:

- Usuari: usuario

- Contrasenya: password

- Base de dades: bbdd

- Domini: localhost

I amb això ja hauries d'haver acabat de configurar i instal·lar la teva base de dades, i ja podries usar perfectament la teva Cloud.

# Configuració d'OwnCloud
Ara pasarem a configurar el nostre [OwnCloud](https://github.com/MichaelAlejo/OwnCloud/blob/main/Cofiguraci%C3%B3%20ownCloud.md)
