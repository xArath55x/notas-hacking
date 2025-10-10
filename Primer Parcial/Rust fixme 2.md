The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee? Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz).

Hints:
https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html

# Solución
Tenemos que arreglar el código de rust. Tenemos que cambiar a que use valores que no sean inmutables, sino que se puedan cambiar a través de su referencia, entonces cambiamos la propia declaración de la variable y cuando se manda como parámetro a la función decrypt
```
let party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?

decrypt(encrypted_buffer, &party_foul); // Is this the correct way to pass a value to a function so that it can be changed?
```
Agregando la palabra reservada mut
```
let mut party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
    
decrypt(encrypted_buffer, &mut party_foul); // Is this the correct way to pass a value to a function so that it can be changed?
```

Después cambiamos como debe de recibir los parámetros la función decrypt
```
fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &String){ // How do we pass values to a function that we want to change?
```
Agregando igualmente la palabra mut
```
fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &mut String){ // How do we pass values to a function that we want to change?
```
Finalmente compilamos y corremos para ver la flag
```
┌──(diego㉿Tallin)-[~/pico/Parcial1GS/Rustfixme2/fixme2]
└─$ cargo build
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.03s
                                                                                                                                                                   
┌──(diego㉿Tallin)-[~/pico/Parcial1GS/Rustfixme2/fixme2]
└─$ cargo run  
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.01s
     Running `target/debug/rust_proj`
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{4r3_y0u_h4v1n5_fun_y31?}
```