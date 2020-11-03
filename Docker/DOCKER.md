# DOCKER

Primer de tot antes de intalar Docker el que farem sera actualitzar els repositoris, una vegada actualizats ya podem fer **sudo apt-get install docker-ce.**

Hara que ya esta instalat farem la primera prova per vore que funciona be, llançarem un contenidor que ens dira “Hello world”.

**sudo docker run hello-world**

![hello](hellodocker.png)

Si volem configurar que el servei de Docker s'inicie al arrancar el sistema farem:

**sudo systemctl enable docker**

I si no volem llevar-lo

**sudo systemctl disable docker**

Hara descargarem com a example uan imatge de Busybox.
Per a descarregar la imatge utilitzarem:

**docker pull Busybox**
![busybox](busybox.png)

Si volem comprobar les imatges que tenim instalades farem un:
docker images

Tambe poder ejecturar comandos com "echo"  y "ls" per exemple.

**docker run Busybox echo "hola world"**
**docker run Busybox ls**
![it](busybox_it.png)

Per a veure els procesos que tenim en marcha podem fer un "ps aux".

**docker run Busybox ps aux**
![public](ps_aux.png)

Si volem llançar més d’una ordre per contenidor, podem fer ús del paràmetre "-it".

**docker run -it Busybox sh**

En el cas que vuigam saber tots el contenidors que tenim podem utilitzar "ps -a".

**docker ps -a**
![public](ps_a.png)

I si volem eliminar alguna imatge fem un "rm" i el id del contenidor: docker rm "i el id del contenidor"

![rm](rm_docker.png)

Tambe podem descarregarmos imatges desde hub.docker.com.
Per a instalar la imatge sols tindrem que buscar la imgatge y agafar el nom de usuari y la imatge,
en este cas seria aixi:

**docker pull prakhar1989/static-site**

![pull](captura.png)

Podem exposar y cambiar els ports del contenido.
docker run -d -P --name static-site prakhar1989/static-site
Funcions:
- d: Separa l’execució del contenidor del terminal
- P: Exposa els ports (aleatoris) a l’exterior
- name: Ens permet donar-li un nom al contenidor

Per vuere el port del contenidor.
**docker port static-site**
![port](port.png)


Podem parar el contenidor, amb el nem dell.
**docker stop static-site**
![stop](parar.png)

Nem a crear un contenidor a partir d’una imatge del servidor web nginx, instalrem.
**docker pull nginx**

El llançem:
**docker  run -d -p 8888:80 nginx nginx_prova nginx**

![run](runstatic.png)

Hara nem a lo que ens interesa que es crear un contenidor per al nostre lloc web de Hugo,
necesitarem agafar la ubicacio de la carpeta public, seria algo aixi:

![public](docker_restaurant.png)
