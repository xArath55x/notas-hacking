Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/214/disk.flag.img.gz)

# Solucion
Descargar el archivo y usar gzip 
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOrchid]
└─$ gzip -d disk.flag.img.gz      
```
Ver las particiones para poder despues listar los archivos 
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOrchid]
└─$ mmls disk.flag.img   
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
```
Listar los archivos y encontrar el archivo flag
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOrchid]
└─$ fls disk.flag.img -o 411648 -r | grep flag
+ r/r * 1876(realloc):  flag.txt
+ r/r 1782:     flag.txt.enc
```
Sabemos que la flag esta encodeada, checamos el historial de comandos para ver como fue encodeada
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOrchid]
└─$ icat disk.flag.img -o 411648 1875
touch flag.txt
nano flag.txt 
apk get nano
apk --help
apk add nano
nano flag.txt 
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
```
Vaciamos el contenido de la flag a un archivo igual pero con .enc
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOrchid]
└─$ icat disk.flag.img -o 411648 1782 > flag.txt.enc
```
Ahora usamos el comando de como encodeo la flag pero con la opcion -d y cambiando los archivos de entrada y salida
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOrchid]
└─$ openssl aes256 -salt -d  -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567 

*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
4017A68E6E7F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:107:
```
Hacer un cat a la flag
```
┌──(diego㉿Tallin)-[~/pico/forensic4/OperationOrchid]
└─$ cat flag.txt      
picoCTF{h4un71ng_p457_1d02081e}                                                                      
```