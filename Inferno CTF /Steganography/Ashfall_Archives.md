# challenge: "Ashfall_Archives"

- If i use this command we can see the passphrase is "**magma**"

```bash
$ stegseek ashfall.jpg /usr/share/wordlists/rockyou.txt
```

**Stegseek will find the password (“magma”) and extract secret.txt.**

- there you have it now you have to use **steghide** with that passphrase to reveal the hidden file:
 
<img width="786" height="169" alt="image" src="https://github.com/user-attachments/assets/88ffe8c2-609a-4645-859c-f1a95294fdd0" />

```bash
$ steghide extract -sf ashfall.jpg
```

- then put you passphrase "magma" and cat the secret.txt file to get your flag 

<img width="341" height="74" alt="image" src="https://github.com/user-attachments/assets/32e4b30a-63fa-4c2d-ad54-ba90ed20649d" />




HAPPY HACKING SOLDIER!!!! 
