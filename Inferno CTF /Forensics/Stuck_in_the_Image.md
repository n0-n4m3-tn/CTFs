# 📄 Solver Write-Up 
# ✅ Challenge: **Stuck in the Image** — Solver
## Category: Forensics
## Points: 50
__________________________________________________
### 🔍 Solution Steps:

- Download the **image** from the challenge.

- Use the **strings** command:

`strings image.jpg | grep flag`

- You’ll see:

<img width="855" height="125" alt="image" src="https://github.com/user-attachments/assets/63b0b374-8831-442c-918d-1ce19d249643" />

**flag{Y0U4R3_4_P1X3l_G3n10us}**


That’s it! The flag was appended to the image file — not visible, but detectable with basic forensics tools.
