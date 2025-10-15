We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.

Hints:
- Try using a tool like Wireshark.
- How can you decrypt the TLS stream?

# Solucion
Entrar a wireshark y ver los paquetes de la captura de paquetes, usar la llave SSH para TSL, descargar la imagen que paso en uno de los paquetes.
Despues ya teniendo la imagen hacer un strings con grep
```
┌──(diego㉿Tallin)-[~/pico/forensic3/WebNet1]
└─$ strings vulture.jpg | grep picoCTF  
picoCTF{honey.roasted.peanuts}
```