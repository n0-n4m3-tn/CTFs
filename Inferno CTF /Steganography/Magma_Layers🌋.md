# Challenge "Magma Layers 🌋"

<img width="487" height="674" alt="image" src="https://github.com/user-attachments/assets/d818d801-9f5e-46e9-b865-9ebc07d3b905" />



- Download the image magma_layers.png: 
use **binwalk** to check embedded files in the image

```bash
$ binwalk magma_layers.png
7279          0x1C6F          Zip archive data, encrypted at least v1.0 to extract, compressed size: 40, uncompressed size: 28, name: secret.txt
```

<img width="1896" height="353" alt="image" src="https://github.com/user-attachments/assets/42689820-eb82-427c-9bcc-01bc7ff3ee5a" />


- we can see there is a zip file hidden we have to extract it:
```bash
$ binwalk -e magma_layers.png
```

- then you cd to the extracted directory:
```bash
$ cd _magma_layers.png.extracted
```

- and unzip : `unzip secret.zip` (oupssss there is a password hahaha)

we can use `strings secret.zip` and we can see this weird string "**LAYERS123**"

<img width="498" height="187" alt="image" src="https://github.com/user-attachments/assets/a8e14f78-0a3c-4075-9bee-5d7439411f91" />

and the try to unzip one more and use that string as the **password** and you'll get your flag


<img width="571" height="82" alt="image" src="https://github.com/user-attachments/assets/a91191dd-ffe3-47c4-a537-184116056fd5" />



H4PPY H4CK1NG!!!
