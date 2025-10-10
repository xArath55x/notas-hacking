## Description

Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.`ssh -p 60916 ctf-player@saturn.picoctf.net`. The password is `fd7746b4`

## Hint

What programs do you have access to?

## Solution

Como los retos anteriores me encuantro con un bash donde los comandos ls y cat no están disponibles. 



```
Specialer$ ls 
-bash: ls: command not found
Specialer$ cat
-bash: cat: command not found
Specialer$ echo hola muno 
hola muno
Specialer$ cd ../ ../
-bash: cd: too many arguments
Specialer$ cd ../ ../home
-bash: cd: too many arguments
Specialer$ cd ../..
Specialer$ cd ../../home
Specialer$ pwd
/home
Specialer$ cd ctf-player/
Specialer$ pwd
/home/ctf-player
Aqui verifico que he avanzado entre carpetas, utilizando el comando pwd y cobnformo que estaba en /home/ctf-player



Specialer$ echo *
abra ala sim
Aqui listo el contenido del directorio actual, lo cuál lo muestro. 




Specialer$ cd abra
Specialer$ echo * 
cadabra.txt cadaniel.txt
Specialer$ echo "$(<cadabra.txt)"
Nothing up my sleeve!
Specialer$ echo "$(<cadaniel.txt)"
Yes, I did it! I really did it! I'm a true wizard!
Entro a la carpeta abra, usé `echo "$(<archivo)"` para leer los archivos, pero no encontre la flag ahí.




Specialer$ pwd
/home/ctf-player
Specialer$ echo *
abra ala sim
Specialer$ cd ala
Specialer$ echo *
kazam.txt mode.tx
Specialer$ echo "$(<kazam.txt)"
return 0 picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_38f5cc78}
Entro a la carpeta ala, que tiene el archivo kazam.txt, donde ahí contenia la flag. 


```


flag -> picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_38f5cc78}