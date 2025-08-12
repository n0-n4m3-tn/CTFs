# Challenge "Leaky Backup"

<img width="490" height="552" alt="image" src="https://github.com/user-attachments/assets/7d441d13-6f64-41bf-9eac-6955da95d458" />

_______________________________________________________________________

- Read the `.txt` file first to learn how to host the website locally and access it via `localhost:8080` :

<img width="482" height="219" alt="image" src="https://github.com/user-attachments/assets/85b95229-80cb-4d46-bcd6-2ae97750247b" />

- Let's check our deer `/robots.txt` :

<img width="191" height="80" alt="image" src="https://github.com/user-attachments/assets/ffe30642-03d7-42ac-92a4-70439dd91406" />

- If we access `/admin.php` we get access denied so let's exfiltrate data at `/backup.zip` then `unzip` the downloaded file and `cat` the data found :

<img width="825" height="477" alt="image" src="https://github.com/user-attachments/assets/253f7b68-e467-4928-a676-5a6a6d0481db" />


Flag: `flag{docker_leaky_backup_456}`
