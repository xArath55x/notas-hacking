[🥛](http://mercury.picoctf.net:58537/)

Hints:
Look at the problem category

# Solucion
Ver pagina fuente, entrar a la hoja de estilos, entrar desde la ruta del sitio a la imagen y descargarla. Usar zsteg para esteganografía. Aumentamos primero el buffer
```
export RUBY_THREAD_VM_STACK_SIZE=50000000
```
Y ahora usar zteg
```
──(diego㉿Tallin)-[~/pico/forensic4/milkslap]
└─$ zsteg -a Untitled.png                    
imagedata           .. text: "\n\n\n\n\n\n\t\t"
b1,b,lsb,xy         .. text: "picoCTF{imag3_m4n1pul4t10n_sl4p5}\n"
```