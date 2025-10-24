Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 48247`.

Hints:
- What kind of encoding uses dashes and dots?
- The flag is in the format PICOCTF{}

# Solucion
Al conectarnos nos da esto en codigo morse
```
┌──(diego㉿Tallin)-[~/pico/Crypto-parte1/Tapping]
└─$ nc jupiter.challenges.picoctf.org 48247 
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. .---- ..--- -.... .---- ....- ...-- ---.. .---- ---.. .---- }
```
Podemos usar la herramienta de cyberchef para decodificar el codigo morse o hacerlo manualmente usando el alfabeto en codigo morse
```
Input: .--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. .---- ..--- -.... .---- ....- ...-- ---.. .---- ---.. .---- }

Recipe: From Morse Code

Output: PICOCTFM0RS3C0D31SFUN1261438181

Flag: PICOCTF{M0RS3C0D31SFUN1261438181}
```