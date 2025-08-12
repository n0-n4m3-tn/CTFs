# Challenge "The Last Whisper"

<img width="491" height="447" alt="image" src="https://github.com/user-attachments/assets/03645f7c-3844-424c-bfa9-f68832c49d8e" />

- Download the given files `clue.txt` and `secret.png`
________________________________________________________________________
### Solution Method 1:

- the clue.txt hints that we could use a **python** script i have a `decode.py` for you :

```python
from PIL import Image

def decode_lsb(image_path):
    img = Image.open(image_path)
    pixels = img.load()
    binary_msg = ""
    
    for y in range(img.height):
        for x in range(img.width):
            r, g, b = pixels[x, y][:3]
            binary_msg += str(r & 1)
            binary_msg += str(g & 1)
            binary_msg += str(b & 1)
    
    # Find the delimiter '1111111111111110' (16 bits)
    delimiter = '1111111111111110'
    if delimiter in binary_msg:
        binary_msg = binary_msg[:binary_msg.index(delimiter)]
    
    # Convert binary to string
    secret = ""
    for i in range(0, len(binary_msg), 8):
        byte = binary_msg[i:i+8]
        secret += chr(int(byte, 2))
    
    return secret

# Usage
print("Extracted message:", decode_lsb("secret.png"))
```

- then execute the script with : `python3 decode.py`

<img width="820" height="87" alt="image" src="https://github.com/user-attachments/assets/dec5cfd0-257e-44b8-adac-d5de12efa6a5" />


### Method 2

- Simple use **zsteg** it's similiar btw to steghide but for `.png` format here's a brief intro to **zsteg**:
`zsteg` is a powerful **steganography tool** for detecting **hidden** data in PNG and BMP images

- use it like this:

```bash
$ zsteg secret.png
```

<img width="1026" height="194" alt="image" src="https://github.com/user-attachments/assets/011c901a-57dd-4459-a576-af88c774fd14" />

