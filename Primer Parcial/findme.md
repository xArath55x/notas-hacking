### Descripcion
Help us test the form by submiting the username as `test` and password as `test!`The website running [here](http://saturn.picoctf.net:62013/).
### Solucion
Como nos habla de redireccionamiento, tenemos que ver lo que hace cada cosa en la pagina, especialmente a donde redirige
Por lo tanto, interceptaremos con burp
Esta es la primera solicitud que capturamos:
``` python
POST /login HTTP/1.1
Host: saturn.picoctf.net:62013
Content-Length: 30
Cache-Control: max-age=0
Origin: http://saturn.picoctf.net:62013
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://saturn.picoctf.net:62013/
Accept-Encoding: gzip, deflate, br
Accept-Language: en,es-MX;q=0.9,es;q=0.8
Connection: keep-alive

username=test&password=test%21
```
no hay un redireccionamiento raro, asi que le daremos forward en burp 
```python
GET /next-page/id=cGljb0NURntwcm94aWVzX2Fs HTTP/1.1
Host: saturn.picoctf.net:62013
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://saturn.picoctf.net:62013/
Accept-Encoding: gzip, deflate, br
Accept-Language: en,es-MX;q=0.9,es;q=0.8
If-None-Match: W/"108-2BEcKhR2MCY0F5SJj/0BG/Qu5b0"
Connection: keep-alive

```
Aqui vemos que hace el primer redireccionamiento a una frase medio rara:
```
cGljb0NURntwcm94aWVzX2Fs
```
esto parece ser un base64, si lo seleccionamos en burp, nos ayuda  a estar seguros de eso
![[Pasted image 20250415131412.png]]
Nos ayuda a ver que es la primera parte de la bander
Le damos forward de nuevo y vemos la siguiente peticion:
```python
GET /next-page/id=bF90aGVfd2F5XzNkOWUzNjk3fQ== HTTP/1.1
Host: saturn.picoctf.net:62013
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://saturn.picoctf.net:62013/next-page/id=cGljb0NURntwcm94aWVzX2Fs
Accept-Encoding: gzip, deflate, br
Accept-Language: en,es-MX;q=0.9,es;q=0.8
If-None-Match: W/"e5-LTjUGH/wFj4zC3orEfBV+FaVEVs"
Connection: keep-alive

```
y vemos el siguiente redireccionamiento 
```
bF90aGVfd2F5XzNkOWUzNjk3fQ
```

Y vemos que es la otra parte de la flag
### Tags
