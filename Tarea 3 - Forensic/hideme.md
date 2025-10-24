Every file gets a flag. The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/256/flag.png).

# Solucion
Una vez descargada la imagen vemos que nada parece extraño, solo cuando hacemos un strings a la imagen
```
secret/flag.pngUT
```
Podemos usar la herramienta de binwalk, que nos ayuda a analizar mas a fondo los binarios de un archivo
```
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/hideme]
└─$ binwalk flag.png          

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 512 x 504, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, compressed
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2997, uncompressed size: 3152, name: secret/flag.png
43036         0xA81C          End of Zip archive, footer length: 22
```
Usamos la opcion -e para generar un nuevo archivo con elementos extraidos
```
──(diego㉿Tallin)-[~/pico/Tarea3Forensic/hideme]
└─$ binwalk -e flag.png 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
41            0x29            Zlib compressed data, compressed
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2997, uncompressed size: 3152, name: secret/flag.png

WARNING: One or more files failed to extract: either no utility was found or it's unimplemented

                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/hideme]
└─$ ls
flag.png  _flag.png.extracted
                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/hideme]
└─$ cd _flag.png.extracted 
                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/hideme/_flag.png.extracted]
└─$ ls
29  29.zlib  9B3B.zip  secret
                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/hideme/_flag.png.extracted]
└─$ cd secret             
                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/…/Tarea3Forensic/hideme/_flag.png.extracted/secret]
└─$ ls
flag.png
```
Abrimos esta imagen y ahi se encuentra la flag
```
flag: picoCTF{Hiddinng_An_imag3_within_@n_ima9e_85e04ab8}
```