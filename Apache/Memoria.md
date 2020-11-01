# Apache
### Açi anem a fer una memoria de com hem instalat el servidor web Apache i com em pujat la nostra web al servidor web.
***


**1. Instalacio del servidor web Apache.**

En primer lloc lo que fem es instalar el servidor web apache. Antes d'això tenim que utilitzar el següent comandament:

~~~
sudo apt update
~~~

Una vegada actualitzada els paquets locals. Veiem si tenim alguna versio del paquet:

~~~
apt-cache policy apache2
~~~

![Veiem l'informació del comandament](/Imatges/aptpolicy.png)

Com veiem el paquet que teniem instalat era el candidat per a instalar, aleshores ens podem votar el següent comandament:

~~~
sudo apt install apache2
~~~

Una vegada instalat, anem al nostre buscador d'Internet i fiquem la nostra adreça localhost. Tindrem que fer-ho amb un buscador desde altre ordinador perque no tenim interficie grafica al servidor.
***

**2. Gestió del servei.**

Per a posar en marxa el servei tenim que fer ús del següent comandament:

~~~
sudo service apache2 start
~~~

I per tal de veure el estat d'ell mateix, ficarem el següent:

~~~
sudo service apache2 status
~~~

Que ens dira com esta funcionant.
***

**3. Modificant el directori /var/wwww/html**

Anem a modificar els permissos d'aquest directori per a que el nostre usuari puga accedir al servidor, a més, també evitar possibles problemes que es pogueren crear de que root fos el propietari d'aquesta.

Primer cnviem el grup propietari de la carpeta amb el següent comandament:

~~~
sudo chgrp www-data /var/www/html
~~~

Una vegada fet el primer pas. Anem a afegir el nostre usuari al grup www-data, fent us del següent comandament:

~~~
sudo usermod -a -G www-data eljust
~~~

I ens donem permissos de forma recursiva amb estos dos comandaments:

~~~
sudo chmod -R 775 /var/www/html
sudo chmod -R g+s /var/www/html
~~~

A mes de afegir-nos com a propietaris d'aquest directori:

~~~
sudo chown -R eljust /var/www/html
~~~
![Permisos dados](/Imatges/permisos.png)
***

**4. Contingut**

Ara anem a pujar el contingut de la carpeta public que varem crear quant exportarem la nostra pagina web desde Hugo.

Jo he copiat tot el contingut que tenia mitjançant el comandament *"scp"*, de la següent forma:

~~~
scp /home/noel/Hugo/Prova/public/* eljust@192.168.1.154:/var/www/html/
~~~
