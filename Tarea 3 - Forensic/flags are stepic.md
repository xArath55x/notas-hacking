A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their message Try it [here](http://standard-pizzas.picoctf.net:51435/)!

Hints:
- In the country that doesn't exist, the flag persists

# Solucion
Visitamos la pagina y vemos que hay muchas banderas. Vemos que hay un pais que es el unico que no tiene bandera, si analizamos el codigo y vemos esto para ese pais
```
{ name: "Upanzi, Republic The",img: "flags/upz.png", style:"width: 120px!important; height: 90px!important;" },
```
Podemos descargar la imagen y analizarla
```
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/FlagsAreStepic]
└─$ wget http://standard-pizzas.picoctf.net:51435/flags/upz.png
--2025-05-13 13:30:12--  http://standard-pizzas.picoctf.net:51435/flags/upz.png
Resolviendo standard-pizzas.picoctf.net (standard-pizzas.picoctf.net)... 3.22.195.189
Conectando con standard-pizzas.picoctf.net (standard-pizzas.picoctf.net)[3.22.195.189]:51435... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 1788400 (1.7M) [image/png]
Grabando a: «upz.png»

upz.png                                  100%[================================================================================>]   1.71M  1.57MB/s    en 1.1s    

2025-05-13 13:30:13 (1.57 MB/s) - «upz.png» guardado [1788400/1788400]

                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/FlagsAreStepic]
└─$ ls
upz.png
                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/FlagsAreStepic]
└─$ exiftool upz.png                                                 
ExifTool Version Number         : 13.10
File Name                       : upz.png
Directory                       : .
File Size                       : 1788 kB
File Modification Date/Time     : 2025:03:05 21:59:39-06:00
File Access Date/Time           : 2025:05:13 13:30:13-06:00
File Inode Change Date/Time     : 2025:05:13 13:30:13-06:00
File Permissions                : -rw-rw-r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 14173
Image Height                    : 10630
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 14173x10630
Megapixels                      : 150.7
```
No se ve nada raro, por el nombre del reto nos da la pista de usar una herramienta llamada stepic, por lo que la usamos y podemos ver la flag
```
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/FlagsAreStepic]
└─$ stepic -d -i upz.png
/usr/lib/python3/dist-packages/PIL/Image.py:3402: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.
  warnings.warn(
picoCTF{fl4g_h45_fl4g3e22f365}                                                                      
```