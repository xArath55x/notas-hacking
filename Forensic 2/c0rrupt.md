## Descripción
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.
## Solución
Vemos que el archivo mystery esta roto, por lo que procedemos arreglarlo Primero poniendo los primeros bytes correctos y que queden como

```
89 50 4E 47 0D 0A 1A 0A
```

Despues cambiar los siguientes chunks que son importantes para que el archivo sea corregido ponemos el chunk IHDR, su codigo ascii

```
49 48 44 52
```

Despues con la herramienta de pngckecker vemos que el chunk de pHYs esta incorrecto, por lo que lo cambiamos tambien

```
cambiar el AA por 00
```

Sigue muy grande entonces cambiamos el chunk IDAT

```
49 44 41 
```

Seguimos cambiando el tamaño poniendo 00 en varios bytes Con esto podemos abrir la imagen y ver la flag

`picoCTF{c0rrupt10n_1847995}`
## Notas
## Referencias