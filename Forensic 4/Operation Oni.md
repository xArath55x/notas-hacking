Download this disk image, find the key and log into the remote machine. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download disk image](https://artifacts.picoctf.net/c/70/disk.img.gz)
- Remote machine: `ssh -i key_file -p 52015 ctf-player@saturn.picoctf.net`

# Solucion 
Primero descargar el archivo y hacer un gzip
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOni]
└─$ gzip -d disk.img.gz  
```
Despues usar mmls para ver las particiones 
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOni]
└─$ mmls disk.img     
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
```
Usar fls para ver los archivos desde inicio hasta la llave privada ssh
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOni]
└─$ fls disk.img -o 206848                    
d/d 458:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 79: proc
d/d 80: dev
d/d 81: tmp
d/d 82: lib
d/d 85: var
d/d 94: usr
d/d 104:        bin
d/d 118:        sbin
d/d 464:        media
d/d 468:        mnt
d/d 469:        opt
d/d 470:        root
d/d 471:        run
d/d 473:        srv
d/d 474:        sys
V/V 33049:      $OrphanFiles
                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOni]
└─$ fls disk.img -o 206848 470
r/r 2344:       .ash_history
d/d 3916:       .ssh
                                                                                                                                                                  
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOni]
└─$ fls disk.img -o 206848 3916
r/r 2345:       id_ed25519
r/r 2346:       id_ed25519.pub
```
Copiar la llave privada a un archivo para luego usarla
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOni]
└─$ icat disk.img -o 206848 2345 > key_file
```
Le cambiamos los permisos al archivo para poder leer solo el propietario
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOni]
└─$ chmod 600 key_file 
```
Finalmente conectarnos con SSH usando el key_file y hacemos cat a la flag
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOni]
└─$  ssh -i key_file -p 52015 ctf-player@saturn.picoctf.net

ctf-player@challenge:~$ cat flag.txt 
picoCTF{k3y_5l3u7h_b5066e83}
```