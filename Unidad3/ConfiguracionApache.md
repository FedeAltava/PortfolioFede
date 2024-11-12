 #Configuración de Apache.

Hoy vamos a dejar la configuración predeterminada del host virtual de **Apache** apuntando a www.example.com y configuraremos nuestro propio sitio en gci.example.com.

Así que empecemos creando una carpeta para nuestro nuevo sitio web en /var/www/ ejecutando.

Ahora que tenemos un directorio creado para nuestro sitio, vamos a añadir un archivo HTML en él. Ingresemos en nuestro directorio recién creado y creemos uno escribiendo:

cd /var/www/gci/
nano index.html

Comenzamos este paso entrando en el directorio de los archivos de configuración:

bash

cd /etc/apache2/sites-available/

Como Apache viene con un archivo de VirtualHost por defecto, usémoslo como base (se usa gci.conf para coincidir con el nombre de nuestro subdominio):

bash

sudo cp 000-default.conf gci.conf

Ahora editemos el archivo de configuración:

bash

sudo nano gci.conf

Debemos poner nuestro correo electrónico en ServerAdmin para que los usuarios puedan contactarnos en caso de que Apache tenga algún error:

apache

ServerAdmin tunombre@example.com

También queremos que la directiva DocumentRoot apunte al directorio donde se alojan los archivos de nuestro sitio:

apache

DocumentRoot /var/www/gci/

El archivo por defecto no incluye una directiva ServerName, por lo que debemos agregarla y definirla añadiendo esta línea debajo de la última directiva:

apache

ServerName gci.example.com

Para configurar nuestro sitio en Apache, entramos al directorio de configuración de VirtualHosts y copiamos el archivo por defecto a uno nuevo llamado gci.conf. Editamos este archivo para agregar nuestro correo electrónico en ServerAdmin, asegurarnos de que DocumentRoot apunte a nuestro directorio del sitio y añadimos la directiva ServerName con el subdominio gci.example.com. Esto garantiza que los usuarios lleguen a nuestro sitio en lugar del predeterminado.

Después de configurar nuestro sitio web, necesitamos activar el archivo de configuración de hosts virtuales para habilitarlo. Lo hacemos ejecutando el siguiente comando en el directorio de archivos de configuración:

bash

sudo a2ensite gci.conf

Deberías ver la siguiente salida:

vbnet

Enabling site gci.
To activate the new configuration, you need to run:
  service apache2 reload

Para cargar el nuevo sitio, reiniciamos Apache escribiendo:

bash

service apache2 reload

Resumen:

Tras configurar el sitio, activamos el archivo de configuración de VirtualHosts usando sudo a2ensite gci.conf y reiniciamos Apache con service apache2 reload para cargar el nuevo sitio. Esto completa la activación del sitio.
