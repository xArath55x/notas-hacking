Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory. [Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz) Access checker program: `nc saturn.picoctf.net 55517`

# Solucion
Descargar el archivo y hacerle un unzip
```
┌──(diego㉿Tallin)-[~/pico/forensic4/SleuthkitIntro]
└─$ gzip -d disk.img.gz 
```
Despues usar la herramienta mmls para saber cuantas particiones, su tamaño, etc
```
┌──(diego㉿Tallin)-[~/pico/forensic4/SleuthkitIntro]
└─$ mmls disk.img  
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```
Despues conectarnos a la instancia con netcat
```
──(diego㉿Tallin)-[~/pico/forensic4/SleuthkitIntro]
└─$ nc saturn.picoctf.net 55517
```
Contestar la pregunta de cual es el tamaño de partición
```
┌──(diego㉿Tallin)-[~/pico/forensic4/SleuthkitIntro]
└─$ nc saturn.picoctf.net 55517
What is the size of the Linux partition in the given disk image?
Length in sectors: 202752
202752
Great work!
picoCTF{mm15_f7w!}
```