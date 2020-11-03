# SERVIDOR APACHE


Primer actualitzarem la llista de paquets del repositori: 

    **$ sudo apt update**
    
Comprovar-em si tenim una instal·lació prèvia del paquet, i quina versió hi ha disponible als repositoris:

    **$ apt-cache policy apache 2**

> Per à comprovar si tenim una instal·lació prèvia del paquet, i quina versió hi ha disponible als repositoris. 

- Vorem que no tenim ninguna verisó instalada, hará instalem en servidor el apache.

    **$ sudo apt intall apache2.** 

> Una vegada instal·lat farem un “ip a” per a veure la ip que tenim y entrarem al servidor apache mitjançant la ip.

## Commandos importants

1. Podem para  o activar el servei mitjançant.

    - **$ sudo systemctl stop apache2 		o		$ sudo service apache2 stop**
    - **$ sudo systemctl star apache2 		o		$ sudo service apache2 star**

2. Si volem consultar l’estat fem:

    - **$ sudo systemctl status apache2 		o		$ sudo service apache2 status**

3. Per a reiniciar el servei farem:

    - **$ sudo systemctl restart apache 2		o		$ sudo service apache2 restart**

4. Si el que volem es recarregar la configuracio perque hem modificat algun parametre podem fer un:

    - **$ sudoo systemctl reload apache2		o		$ sudo service apache2 reload**


# Directori /var/www/html

- Ara anem a cambiar el grup propietari de la carpeta /var/www/html a www-data: 

    **$ sudo chgrp www-data /var/www/html** 

![chgrp](images/chgrp.png)

- I afegim el nostre usuari a aquest grup: 

    **$ sudo usermod -a -G www-data eljust**

![usermod](images/usermod.png)
 
- Donem els següent permissos de forma recursiva:

    **$ sudo chmod -R 775 /var/www/html**
    **$ sudo chmod -R g+s /var/www/html**

![chmod](images/chmod.png)

- També ens afegim com als propietaris d’aquest directori, per poder treballar amb ell:

    **$ sudo chown -R eljust /var/www/html**

![chown](images/chown.png)

- Ara crearem una carpeta public amb la funció “Hugo -D” en l’atra maquina virtual on tenim la pagina web, canviarem la direcció  de la pàgina web situada en “config.yaml” a la ip del servidor Apache.

    **$ Hugo -D**

![Hugo-d](images/hugo-d.png)



- Hará tindrem que copiar la carpeta públic a la direcció /var/www/html del servidor Apache, y entrar en internet amb la direccio 192.168.1.58 per a comprovar  si està tot correcte.

    **$ scp -r public/* eljust@192.168.1.58:/var/www/html**

![srcp](images/scp.png)

![public](images/public.png)