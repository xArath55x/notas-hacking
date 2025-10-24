Decrypt this [message](https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext).

Hint:
caesar cipher [tutorial](https://learncryptography.com/classical-encryption/caesar-cipher)

# Solucion
Tenemos un mensaje que se tiene que decifrar por el algoritmo cesar, que funciona relacionando el abecedario con este mismo pero desplazado n numero de posiciones
```
mensaje: picoCTF{gvswwmrkxlivyfmgsrhnrisegl} 
```
Podemos usar cyberchef para intentar descifrarlo, usando ROT13 que rota el mensaje para descifrar
```
Input: gvswwmrkxlivyfmgsrhnrisegl

Recipe: ROT13 - 25 rotaciones

Output: picoCTF{crossingtherubicondjneoach}
```