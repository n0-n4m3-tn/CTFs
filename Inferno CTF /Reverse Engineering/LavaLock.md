# Challenge "LavaLock"
## Description: Buried deep beneath Mount Inferno lies a machine locked by ancient code. Only those who can reverse its logic will unlock the secret it guards. Can you crack the LavaLock and control the flow?

Download the File and Run it with `./lavalock`
__________________________________________________

when we run the file with `./lavalock` it should look like this: 

<img width="1397" height="128" alt="image" src="https://github.com/user-attachments/assets/5aadec37-b7e6-4641-8236-4c30eee35420" />

we have to find the key ; when we input for example **"key"** as input :

<img width="1225" height="154" alt="image" src="https://github.com/user-attachments/assets/af4cc32c-3b2c-4f2d-a838-c4d771630e19" />

nope unfortunately we can't go in let's try something else ; could be something hidden in strings we use this command :

 `strings lavalock`

 we find something interesting a weird string : `"Inferno123"`

 <img width="421" height="112" alt="image" src="https://github.com/user-attachments/assets/d9e21278-ba67-4fcb-8df4-ccc629207865" />

 let's try it as a **key**:
 
 <img width="1459" height="219" alt="image" src="https://github.com/user-attachments/assets/15665f8a-a236-4dee-93e7-75d2d4e2a983" />

yup :) our guess was right there is your flag soldier :))
