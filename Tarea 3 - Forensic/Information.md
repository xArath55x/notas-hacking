Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/d1375e383810d8d957c04eef9e345732/cat.jpg)

Hints:
	- Look at the details of the file
	- Make sure to submit the flag as picoCTF{XXXXX}

# Solucion
Descargamos la imagen y la podemos analizar con exiftool
```
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/information]
└─$ exiftool cat.jpg 
ExifTool Version Number         : 13.10
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2021:03:15 12:24:46-06:00
File Access Date/Time           : 2025:05:13 13:35:04-06:00
File Inode Change Date/Time     : 2025:05:13 13:35:04-06:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```
Vemos que en la licencia se encuentra algo un poco raro, podemos intentar descifrarlo de base64
```
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/information]
└─$ echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d    
picoCTF{the_m3tadata_1s_modified}       
```
Y asi podemos ver la flag