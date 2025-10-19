Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/138/disk.flag.img.gz)

# Solucion
Descargar el archivo y hacerle un unzip 
```
┌──(diego㉿Tallin)-[~/pico/forensic4/SleuthkitApprentice]
└─$ gzip -d disk.flag.img.gz 
```
Despues podemos ver las particiones para ver donde estan los archivos
```
┌──(diego㉿Tallin)-[~/pico/forensic4/SleuthkitApprentice]
└─$ mmls disk.flag.img         
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
```
Despues usar fls para listar los archivos de la imagen recursivamente para encontrar un archivo flag en cualquier lado
```
┌──(diego㉿Tallin)-[~/pico/forensic4/SleuthkitApprentice]
└─$ fls disk.flag.img -o 360448 -r | grep flag
++ r/r * 2082(realloc): flag.txt
++ r/r 2371:    flag.uni.txt
```
usar icat para hacer un cat al archivo flag
```
┌──(diego㉿Tallin)-[~/pico/forensic4/SleuthkitApprentice]
└─$ icat disk.flag.img -o 360448 2371
picoCTF{by73_5urf3r_2f22df38}
```