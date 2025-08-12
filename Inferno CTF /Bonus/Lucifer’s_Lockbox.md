# Challenge "Lucifer’s Lockbox"

<img width="490" height="550" alt="image" src="https://github.com/user-attachments/assets/0f5df5c3-514c-4330-9094-958d2c6c33b6" />

__________________________________________________________________________________________

## Solution:

- This is decryption script create it on your box and execute it with `python3 decrypt.py` :

```python
import hashlib

def hellfire_decrypt(encrypted, key):
    decrypted = []
    for i, c in enumerate(encrypted):
        key_part = ord(key[i % len(key)])
        hell_shift = (c - key_part - i) % 256  # Reverse the encryption
        decrypted.append(hell_shift)
    return bytes(decrypted)

def main():
    # Key is SHA256("InfernoCTF") first 8 chars
    secret_key = hashlib.sha256(b"InfernoCTF").hexdigest()[:8]

    with open('lockbox.bin', 'rb') as f:
        data = f.read()

    # Remove garbage (only first N bytes matter)
    encrypted = data[:len(data) - 100]  # Remove last 100 bytes

    decrypted = hellfire_decrypt(encrypted, secret_key)
    print(decrypted.decode())

if __name__ == "__main__":
    main()
```

<img width="864" height="114" alt="image" src="https://github.com/user-attachments/assets/bb72ce68-a197-4398-8301-8c6d981e659f" />


Flag: `InfernoCTF{7h3_k3y_w45_1n_7h3_4byss_4ll_4l0ng}`
