# Challenge "Wake Up 1.0"
## Description: "Did you pay attention some images hide something BUT WHERE??...that's all im gonna say :)"
_________________________________________________________________________________________________________________

ok lemme give you this straight this challenge requires a lot of attention, did you focus on the **1+1=?** challenge the flag was obvious but he gave you also a useless image called `hihi.jpg`.
Do you actually think that he done that to fool you oh no buddy !! :))

<img width="489" height="494" alt="image" src="https://github.com/user-attachments/assets/96f5d9ad-8936-461f-83a9-0fe7271f9bf7" />

- Download the image `hihi.jpg` and check it metadata with `exiftool`:

<img width="1125" height="141" alt="image" src="https://github.com/user-attachments/assets/7c8725ce-c603-4eaf-b95f-a21cbc44af97" />

- well that's a fucking base64 let's decode it: 
```
└─$ echo cDFzc3cwckQxMjM= | base64 -d                     
p1ssw0rD123
```
- then use `steghide` : `steghide extract -sf hihi.jpg`

- input the password you found and booommmm!! :))

<img width="718" height="352" alt="image" src="https://github.com/user-attachments/assets/e4fdc058-38fe-43c3-bd9f-042038f98955" />
