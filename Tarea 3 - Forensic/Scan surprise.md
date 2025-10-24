I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?
You can download the challenge files here:
challenge.zip

The same files are accessible via SSH here:`ssh -p 55423 ctf-player@atlas.picoctf.net`Using the password `1ad5be0d`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

Hints:
- QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
- Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
- If you don't have access to a phone, you can also use zbar-tools to convert an image to text

# Solución
Conectarse y hacer un zbarimg al archivo png del código qr
```
ctf-player@challenge:~/drop-in$ zbarimg flag.png       

Resultado:
Connection Error (Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory)
Connection Null
QR-Code:picoCTF{p33k_@_b00_b5ce2572}
scanned 1 barcode symbols from 1 images in 0.01 seconds
```
