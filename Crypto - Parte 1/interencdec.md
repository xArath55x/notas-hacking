Can you get the real meaning from this file. Download the file [here](https://artifacts.picoctf.net/c_titan/1/enc_flag).

Hints:
- Engaging in various decoding processes is of utmost importance

# Solucion
Descargamos el archivo y nos da esta cadena
```
┌──(diego㉿Tallin)-[~/pico/Crypto-parte1/interencdec]
└─$ cat enc_flag  
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyeG9OakJzTURCcGZRPT0nCg==
```
Sabemos que esta en base64 porque termina en guiones
podemos quitarle el base64 para iniciar
```
┌──(diego㉿Tallin)-[~/pico/Crypto-parte1/interencdec]
└─$ echo YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyeG9OakJzTURCcGZRPT0nCg== | base64 -d
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2xoNjBsMDBpfQ=='
```
Vemos que sigue en base64 entonces repetimos el quitarle base64
```
┌──(diego㉿Tallin)-[~/pico/Crypto-parte1/interencdec]
└─$ echo d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX2xoNjBsMDBpfQ== | base64 -d
wpjvJAM{jhlzhy_k3jy9wa3k_lh60l00i}  
```
Ya con esto podemos ir a cyberchef y usar el algoritmo de ROT13 para darle vueltas, vemos que con 19 vemos la flag
```
Input: wpjvJAM{jhlzhy_k3jy9wa3k_lh60l00i}

Recipe: ROT13 - 13 veces

Output: picoCTF{caesar_d3cr9pt3d_ea60e00b}
```