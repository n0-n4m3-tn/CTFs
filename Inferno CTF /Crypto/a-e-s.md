# Challenge "a-e-s"

**"It hints already by the name that the algorithm of the encryption is aes"**

```
file encrypted.bin    
encrypted.bin: data
```
that's our encrypted file 
but we have another file `unknown.txt`

hmmmm let's cat it : 
```
cat unknown.txt  
354247422659484e37554a4d28494b3c
```
it's probably the **key** to decrypt our data and for that To decrypt the file (encrypted.bin) let's use `OpenSSL` with the given key:
`openssl enc -d -aes-128-cbc -in encrypted.bin -out decrypted.file -K "354247422659484e37554a4d28494b3c" -iv "00000000000000000000000000000000"`
`-d`: Decrypt mode.

`-aes-128-cbc`: Encryption algorithm (adjust if needed).

`-in encrypted.bin`: Input file.

`-out decrypted.file`: Output file.

`-K`: Key in hex.

`-iv 00000000000000000000000000000000`: Use a null IV (if no IV is provided).


then `cat` the **decrypted.file** you'll get your flag soldier!!

<img width="649" height="83" alt="image" src="https://github.com/user-attachments/assets/80b21108-2153-4c8a-bbab-7d843860b330" />



HAPPY HACKING!!!💀
