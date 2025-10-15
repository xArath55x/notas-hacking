We found this [file](https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n). Recover the flag.

Hints:
	Weird that it won't display right...

# Solucion 
Arreglar el archivo cambiando los encabezados en la direccion de inicio de los datos y en el tamaño del encabezados 
a 0x28 y el tamaño de la imagen a 0x40 para que se vea mas grande y se vea la flag
```
picoCTF{qu1t3_a_v13w_2020}
```