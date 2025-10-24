The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?

Hints:
	The flag is in the format PICOCTF{}

# Solución
Podemos ver que la imagen son numeros, sabemos que una de las tecnicas de encriptación es la relación entre números y letras 

Entonces podemos asociar el inicio de la flag con los primeros numeros
```
16 9 3 15 3 20 6
p  i c o  C  T F
```
Y asi debemos de cada letra asignar un numero y ver la flag segun los numeros
Entonces podemos automatizar esto, primero anotamos todos los numeros que estan ahi 
```
16 9 3 15 3 20 6 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14
```
Teniendo esto podemos pasarlo a cyberchef, usando la varita magica y nos recomienda usar un cifrado especifico
```
input: 16 9 3 15 3 20 6 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14

Recipe: A1Z26 Cipher Decode

output: picoctfthenumbersmason
```
Flag
```
picoCTF{thenumbersmason}
```