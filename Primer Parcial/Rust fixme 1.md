Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag! Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz).

Hints:
- Cargo is Rust's package manager and will make your life easier. See the getting started page [here](https://doc.rust-lang.org/book/ch01-03-hello-cargo.html)
- [println!](https://doc.rust-lang.org/std/macro.println.html)
- Rust has some pretty great compiler error messages. Read them maybe?

# Solución
Tenemos que arreglar la sintáxis del código de rust.
Primeramente el como acabas una linea:
```
let key = String::from("CSUCKS") // How do we end statements in Rust?
```
Ponemos punto y coma 
```
let key = String::from("CSUCKS"); // How do we end statements in Rust?
```
Después como hacer return en rust:
```
    let res = XORCryptor::new(&key);
    if res.is_err() {
        ret; // How do we return in rust?
    }
    let xrc = res.unwrap();
```
Ponemos return
```
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return; // How do we return in rust?
    }
    let xrc = res.unwrap();
```
Finalmente como imprimimos algo dentro de la función de println
```
    println!(
        ":?",  // How do we print out a variable in the println function? 
        String::from_utf8_lossy(&decrypted_buffer)
    );
```
Ponemos llaves, así es como se imprime:
```
    println!(
        "{}",  // How do we print out a variable in the println function? 
        String::from_utf8_lossy(&decrypted_buffer)
    );
```
Finalmente compilamos el código 
```
┌──(diego㉿Tallin)-[~/pico/Parcial1GS/Rustfixme1/fixme1]
└─$ cargo build 
   Compiling rust_proj v0.1.0 (/home/diego/pico/Parcial1GS/Rustfixme1/fixme1)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.37s
```
Y lo corremos
```
┌──(diego㉿Tallin)-[~/pico/Parcial1GS/Rustfixme1/fixme1]
└─$ cargo run  
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.01s
     Running `target/debug/rust_proj`
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}
```