# Challenge : 'Inferno Gatekeeper'
## Description : 🔥 The path to the volcano’s heart is guarded by a Gatekeeper. He only reveals the secrets to those who appear to be him... Can you trick the system into letting you in?

⚠️ Run this challenge locally using: `docker-compose up -d`
_____________________________________________________________________



unzip the file given then `cd` to **Inferno_Gatekeeper**
Run `docker-compose up -d`.
Open your browser and navigate to: `http://localhost:31337`


<img width="496" height="189" alt="image" src="https://github.com/user-attachments/assets/74fd6836-c6e9-4ed1-a775-e17ee49d786a" />




1. login with admin:admin (But… logging in isn't enough. hahahahah)


<img width="372" height="208" alt="image" src="https://github.com/user-attachments/assets/4152d1bf-4a8e-456d-9cc5-2e405ec8a965" />


2. Opens browser dev tools → Application → Cookies.
3. Edits `is_admin=false` → `is_admin=true`.

<img width="1914" height="926" alt="image" src="https://github.com/user-attachments/assets/d7ca72c4-deb1-4939-9bd4-2de3bad51e03" />

4. Refreshes `/admin` → Flag revealed.

<img width="456" height="150" alt="image" src="https://github.com/user-attachments/assets/7503d12b-a61e-414c-ba87-cb5548360858" />



-> **flag{volcanic_cookie_trickery}** HAPPY HACKING !!!! 

