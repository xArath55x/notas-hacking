## Descripción
Decode this [message](https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav) from the moon.
## Solución
Una vez teniendo en audio en formato wav. Podemos descargar una herramienta para decodificar una imagen a partir del audio. Usando SSTV. Decodificamos:

```
└─$ sstv -d message.wav -o resultado.png
[sstv] Searching for calibration header... Found!    
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...                                [####################################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```

Y obtenemos la imagen de donde podemos sacar la flag Flag:

```
picoCTF{beep_boop_im_in_space}
```
## Notas
## Referencias