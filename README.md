# Bieel-Manjon.pt2
# Instal·lació d'OwnCloud

## Instal·lació de la versió 7.4 de PHP a Ubnutu 24.04

Per a instal·lar OwnCloud necessitem la versió 7.4 de PHP.

Aquestes son les comandes per a actualitzar el PHP.

Amb la comanda instal·lem els requisits de PPA.

```bash

sudo apt install software-properties-common -y

```

Instal·lem lo necessàri per a poder treballar amb PPA.

```bash

LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y

```

Actualitzem tot

``` bash

sudo apt update

```

Amb aquestes 3 comandes instal·lem les llibreries de PHP 

``` bash

sudo apt install php7.4 -y

```

``` bash

sudo apt install -y php libapache2-mod-php7.4

```

``` bash

sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl

```

Amb aquesta comanda seleccionem la versió de PHP la 7.4.

``` bash

sudo update-alternatives --config phpmmm

```

Ara activem els mòduls necessaris d'Apache2 perquè funcioni.

``` bash

sudo a2enmod proxy_fcgi setenvif

```

``` bash

sudo a2enconf php7.4-fpm

```

Y per finalitzar amb l'instal·lació de la versió 7.4 de PHP, reiniciarem l'Apache2.

``` bash

sudo service apache2 restart

```

## Comandes per l'instal·lació i configuració de OwnCloud

Per a instal·lar i configurar OwnCloud, utilitzarem d'apache2, al instal·lar Apache2 es crearà una carpeta dins de /var/www/html, on treballarem.

## Comandes per l'instal·lació d'Apache2 i mysql, i llibreries de PHP

Actualitzem la màquina.

``` bash

sudo apt update

```

Aixo NO és obligatòri posar-ho , però és millor, a més que triga molt en processar la comanda.

``` bash

sudo apt upgrade

```

Instal·lem el servidor web d'Apache2

``` bash

sudo apt install -y apache2

```

Instal·lem la base de dades mysql

``` bash

sudo apt install -y apache2

```

Instal·lem llibreries PHP, que aquest és el llenguatge de les aplicacions.

``` bash

sudo apt install -y php libapache2-mod-php

```

``` bash

sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl

```

I per finalitzar reiniciem el servidor d'Apache2 amb aquesta comanda

``` bash

sudo systemctl restart apache2

```

## Configurem la base de dades de mysql

### Entrem a la consola de dades de mysql.

Des d'un terminal posem aquesta comanda per entrar a la terminal de mysql

``` bash

sudo mysql

```
![Captura desde 2024-11-07 14-06-07(1)](https://github.com/user-attachments/assets/a0477b29-fd8f-4859-8ee9-8aabf9b613f3)

### Creem una base de dades.

Dins de mysql creem una base de dades,i li posem el nom de bbdd

``` bash

CREATE DATABASE bbdd;

```
![Captura desde 2024-11-07 14-06-20](https://github.com/user-attachments/assets/ab8def8a-e326-4a43-b230-16809fb4167f)

### Creació del  usuari

Ara crearem un nou usuari, a més que utilitzarem la IP de localhost

``` bash

CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

```
![Captura desde 2024-11-07 14-06-57](https://github.com/user-attachments/assets/d1611068-eeaf-4d1d-b109-e6531834f477)

### Li donem privilegis al nostre usuari abans de finalitzar

``` bash

GRANT ALL ON bbdd.* to 'usuario'@'localhost';

```
![Captura desde 2024-11-07 14-07-08](https://github.com/user-attachments/assets/e0b44991-d29e-46e2-a0d7-18a94b98d391)

### Sortim de la base de dades

``` bash

exit

```

### TOot els pasos estan bé?.

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

Descomprimim el .zip que hem baixat.

``` bash

sudo unzip owncloud-complete-20240724.zip

```

Copiem els fitxers a la carpeta /var/www/html, i canviem els signes d'interrogant (?) pel nom del directori on s'ha descomprimit l'arxiu d'abans.

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

## Permisos a les aplicacions web.

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

Entro a http://localhost en el teu navegador web, i configura la teva Cloud.

#### Si heu fet bé tots els passos, us ficarà al OwnCloud, i us demanarà crear-vos un usuari d'admin i la base de dades que has configurat.

La  informació:

- Usuari: usuario

- Contrasenya: password

- Base de dades: bbdd

- Domini: localhost

I amb això ja esta configurat i instal·lat la base de dades.

# Configuració d'OwnCloud
Ara pasarem a configurar el nostre [OwnCloud]

<p>Si has fet tot els pasos d'abans bé ahuries d'estar aqui

  
## BORRAR CAMBIAR CAPTURAS   
## BORRAR CAMBIAR CAPTURAS   
## BORRAR CAMBIAR CAPTURAS   
## BORRAR CAMBIAR CAPTURAS   
## BORRAR CAMBIAR CAPTURAS   


![Captura desde 2024-11-12 08-36-23](https://github.com/user-attachments/assets/c679aa8f-b595-490b-bd02-a94b38cbba67)

## Creació d'usuaris
<p>Per crear usuaris anem a la part dreta on surt el nostre usuari i cliquem.

![Captura desde 2024-11-12 08-38-12](https://github.com/user-attachments/assets/4942a1f6-0be6-4644-be9b-dc00ff0595c7)
<p>Aqui cliquem on posa "users".
  
![Captura desde 2024-11-12 08-39-36](https://github.com/user-attachments/assets/1d38c658-3cd8-4e1c-ba9a-7e43ce801ea5)
<p>I aqui es on creem els usuaris.
<p>Per crear el usuari tenim que posar el nom de l'usuari, i un e-mail, que pot ser inventat.
<p>Aixo es fa en l'espai de dalt del teu usuari que posa el que he dit abans.
  
![Captura desde 2024-11-12 08-43-09](https://github.com/user-attachments/assets/a0487e98-c3f0-4e42-9fd3-b44ef4b53575)
<p>Ara creem 3 o 4 usuaris.
  
![Captura desde 2024-11-12 08-52-23](https://github.com/user-attachments/assets/6b3332ea-27cc-47d8-9444-bf80ffd0b6bd)
## Assignem rols i permisos
<p> Ara assignarem rols al nostres usuaris creats.
<p> Per crear un rol li tenim que clicar on posa "Add group", i tindras ja dos rols creats predeterminats, "Everyone" i "Admin".
  
![Captura desde 2024-11-12 08-57-00](https://github.com/user-attachments/assets/e74ad03a-7c27-4017-8729-3c131b37c6e5)
<p>I creem dos rols nous, els que vulguis.
<p>Per assignar els rols en un usuari li donem a "Group" en el mateix usuari i l'assignem el rol que acabem de crear.
<p>I ahuria de quedar aixi amb el nom dels rols creats per tu.
  
![Captura desde 2024-11-12 09-04-21](https://github.com/user-attachments/assets/a5ade8fe-e0fc-4842-a09b-3f475ed73654)
<p>Ara assignem permisos al nostres usuaris.
<p>Li donem a "users" que posa d'alt del tot, i aqui donem a "Archivos"
<p>Aqui seleccionem la carpeta a que volem donar permisos als nostres usuaris.
<p> I li donem a "sharing", posem el nom dels rols que volem donar permisos a aquesta carpeta, o el nom de l'usuari al que volem donar permisos en aquesta carpeta.
<p>I amb els teus rols i usuaris ahuria de quedar aixi
  
![Captura desde 2024-11-12 09-23-02](https://github.com/user-attachments/assets/a0cecf31-4afb-426e-a607-99d41497a1ae)
<p>I si li donem al engranatge al costat del usuari o rol, podem posar que pot fer aquest grup o persona. 
  
![Captura desde 2024-11-12 09-25-46](https://github.com/user-attachments/assets/eae7ab17-c2b4-4360-9972-63722246f288)
<p>I amb aixo ja ahuriem d'haver acabat de configurar rols i permisos als rols.
# Administració d'arxius.
<p>Per crear arxius, carpetes o pujar fitxers, em de donarle al "+" que posa dalt de les carpetes predeterminades.
  
![Captura desde 2024-11-12 09-40-19](https://github.com/user-attachments/assets/bc3ea617-71bd-49c2-9858-7d747505c964)
<p>I creem una carpeta amb qualsevol nom.
<p> Ara creem un arxiu dins de la carpeta 
  
![Captura desde 2024-11-12 09-42-49](https://github.com/user-attachments/assets/6c899237-e4d3-4e4a-b84e-e9728ff47396)
<p>I aquest arxiu serveix com un document, pots escriure el que vulguis dins.
<p>També pots pujar un arxiu desde la teva propia maquina.
<p>I dins de l'arxiu com en les carpetes, també pots donar permisos a usuaris d'editar els arxius o pujar mes arxius.
