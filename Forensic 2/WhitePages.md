## Descripción
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://jupiter.challenges.picoctf.org/static/fa4a277cfa846e07a5981d8a19288a2e/whitepages.txt) is all blank!
## Solución
Tenemos un archivo en unicode con espacios en blanco, de dos tipos. Podemos cambiar estos dos tipos de espacios a ceros y unos usando la libreria de pwntools con python, cambiar los espacios a ceros y unos y luego decodificar a ascii para ver la flag Codigo:

```
from pwn import *

file = open('whitepages.txt', 'rb')
data = bytearray(file.read())
data = data.replace(b'\xe2\x80\x83', b'0')
data = data.replace(b'\x20', b'1')
data = data.decode('ascii')
data = unbits(data)
print(data)
```

Mensaje con flag:

```
┌──(venv)─(diego㉿Tallin)-[~/pico/forensic2/WhitePages]
└─$ python exp.py
b'\n\t\tpicoCTF\n\n\t\tSEE PUBLIC RECORDS & BACKGROUND REPORT\n\t\t5000 Forbes Ave, Pittsburgh, PA 15213\n\t\tpicoCTF{not_all_spaces_are_created_equal_3e2423081df9adab2a9d96afda4cfad6}\n\t\t'
```
## Notas
## Referencias