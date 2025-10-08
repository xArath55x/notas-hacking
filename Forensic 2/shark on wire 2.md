## Descripción
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.
## Solución
Podemos analizar la captura de paquetes que nos proporcionan con el programa de wireshark, de tal manera que nos damos cuenta de que a partir de tal paquete viene la palabra start y ciertos paquetes despues vemos la palabra end. Esto nos indica algo interesante, podemos ver que a partir de start si a cada puerto de la fuente le restamos 5000 y vemos su codigo ascii es una letra y vemos que asi se forma la flag Usando la libreria de scapy de python podemos construir la flag, código:

```
from scapy.all import *

packets = rdpcap('capture.pcap')

flag = ''

for p in packets:
    if UDP in p and p[UDP].dport == 22:
        if p[UDP].sport > 5000:
            flag += chr(p[UDP].sport - 5000)
print(flag)
                 
```

Flag:

`picoCTF{p1LLf3r3d_data_v1a_st3g0}`
## Notas
## Referencias