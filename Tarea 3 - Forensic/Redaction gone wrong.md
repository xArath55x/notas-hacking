Now you DON’T see me. This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?

Hints:
How can you be sure of the redaction?

# Solucion
Podemos descargar el pdf y vemos que ciertas partes estan tapadas, podemos usar la herramienta de pdftotext
```
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/redactionGoneWrong]
└─$ pdftotext Financial_Report_for_ABC_Labs.pdf 
```
Ya teniendolo en txt podemos filtrar por la palabra picoCTF con grep
```
┌──(diego㉿Tallin)-[~/pico/Tarea3Forensic/redactionGoneWrong]
└─$ cat Financial_Report_for_ABC_Labs.txt | grep picoCTF
picoCTF{C4n_Y0u_S33_m3_fully}
```