# Challenge "Winik ya ghZellla?"

<img width="488" height="525" alt="image" src="https://github.com/user-attachments/assets/fb3a2ae6-b10c-4fc0-a3cf-e3e95b3902f6" />
________________________________________________

## Solution
- Download the image `ghZella.bmp`
- use steghide to reveal hidden data :

```bash
$ steghide extract -sf ghZella.bmp
```

<img width="711" height="124" alt="image" src="https://github.com/user-attachments/assets/82d17cfb-39b4-47a7-a824-de8c699ce883" />

- we have a zip file `secret.7z`

<img width="802" height="91" alt="image" src="https://github.com/user-attachments/assets/c6fbdc09-af3a-4dc2-8980-f287fc24a47d" />

- when you try to extract with `$ 7z x secret.7z` it requires a password

<img width="678" height="47" alt="image" src="https://github.com/user-attachments/assets/0cd10495-b5b8-4117-9fb9-d2400a184048" />

- but when we come back and check `strings` of the image `ghZella.bmp` we find a fake flag and trust me it is right there for a reason buddy :

```bash
$ strings ghZella.bmp
```

<img width="370" height="39" alt="image" src="https://github.com/user-attachments/assets/2c181552-5f98-4566-b4c8-5a161da77511" />

- The password is actually that fake flag haha and precisely `m4ll4_ghZ3ll4` let's try to extract now:

```bash
$ 7z x secret.7z
```

<img width="480" height="449" alt="image" src="https://github.com/user-attachments/assets/a3d91e46-a5ef-4874-8e7c-b7ec5f873e33" />

- We find a pdf file let's open it and get our flag:

<img width="846" height="115" alt="image" src="https://github.com/user-attachments/assets/79632543-32fe-4d7b-9d16-5cdb55147f34" />


ENJOY :)))


