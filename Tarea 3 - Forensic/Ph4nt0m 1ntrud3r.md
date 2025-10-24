A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag. To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder! Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/b6fbb3a5560749f838cdc6db4950985767c4691db3a7b34a220e5654ee39e700/myNetworkTraffic.pcap) and try to get the flag.

Hints:
- Filter your packets to narrow down your search.
- Attacks were done in timely manner.
- Time is essential

# Solucion
Descargamos el archivo .pcap y usamos wireshark para analizar los paquetes 
Podemos filtrar los paquetes de tamaño 12 y vemos que por su contenido hexadecimal crea cadenas que podemos tomar, juntar y descifrar. Estas las ordenamos siguiendo el tiempo cronologico de como se mandaron:
```
cGljb0NURg==ezF0X3c0cw==bnRfdGg0dA==XzM0c3lfdA==YmhfNHJfMw==NmY0YTY2Ng==
```
Vemos que esta en base64 y podemos descifrarla:
```
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/ph4nt0m1ntrud3r]
└─$ echo cGljb0NURg==ezF0X3c0cw==bnRfdGg0dA==XzM0c3lfdA==YmhfNHJfMw==NmY0YTY2Ng== | base64 -d
picoCTF{1t_w4snt_th4t_34sy_tbh_4r_36f4a666}               
```