
## Description
There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/64e724ad327f83ad833d9c6baa072b1f/store.c). Connect with `nc jupiter.challenges.picoctf.org 4906`.

## Hint

1. Two's compliment can do some weird things when numbers get really big!

## Solution

Nos conectamos al servidor y descargamos el archivo: 

```
(lalosan㉿lalosan)-[~/exam1p1]
─$  nc jupiter.challenges.picoctf.org 4906.
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

```

Nos ofrece tres opciones, pero la que nos interesa es la segunda.

Abrimos el archivo c, para analizar el código y encontrar una vulnerabilidad.


```
if(number_flags > 0){
                    int total_cost = 0;
                    total_cost = 900*number_flags;
                    printf("\nThe final cost is: %d\n", total_cost);
                    if(total_cost <= account_balance){
                        account_balance = account_balance - total_cost;
                        printf("\nYour current balance after transaction: %d\n\n", account_balance);
                    }
                    else{
                        printf("Not enough funds to complete purchase\n");
                    }
                                    
                    
                }

```

Se observa que la bandera falsa cuesta 900. y se le reata el costo total_cost del saldo.
Qué pasaría si esta variable fuera negativa, esta fue declarada como int, esto es un entero con signo, por lo cual su rango  es de (-2147483648 y 214748364), los enteros usa con con signo el primer bit para indicar si es positivo o negativo. Le sumamos 1 a 2,147,483,647 y se convierte en negativo, esta es una técnica como desbordamiento de entero, así a total_cost desborde a número negativo y así aumentar el saldo. 

![[Pasted image 20250416082424.png]]
 Se necesita que total cost ssea un número negativo grande, pero no tanto para que debord el account:balance. Se va utilizar el 3000000