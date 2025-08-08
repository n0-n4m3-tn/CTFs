# Challenge "Secret Vault"

Let's run the file like he told us:

<img width="1489" height="211" alt="image" src="https://github.com/user-attachments/assets/d3e4f651-6665-4dae-b467-606f487cdebb" />

we found a weird text that looks like a hash: ```35cd6c36d4e1670b663b4898bd605454d9b32f36523d13451811850556ef4b86```
let's run this command : ```hashid -m -j 35cd6c36d4e1670b663b4898bd605454d9b32f36523d13451811850556ef4b86```
just to check the **hashing algorithm**

<img width="1268" height="368" alt="image" src="https://github.com/user-attachments/assets/3545918c-dd0c-4c55-b947-f6055ad19336" />

- then let's save it in a file `hash.txt`

<img width="1350" height="115" alt="image" src="https://github.com/user-attachments/assets/3707e8f0-abc9-487c-ad01-5998413605ce" />

- now it's time to crack the **hash** with `johntheripper`:

<img width="1492" height="332" alt="image" src="https://github.com/user-attachments/assets/706e05d8-c052-4723-8988-2a813d7739d2" />

- use that string you got in the program executed you should get your flag:

<img width="1473" height="248" alt="image" src="https://github.com/user-attachments/assets/6f891c2c-56b0-4d16-9a5f-44a750f5d619" />
