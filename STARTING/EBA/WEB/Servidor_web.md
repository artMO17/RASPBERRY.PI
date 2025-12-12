Nginx

👉 Ventaja clave:
NO tengo que abrir puertos en mi router, así que mi red queda protegida.

Arquitectura (muy importante entender esto)
Internet
   ↓
Cloudflare (HTTPS, WAF, DNS)
   ↓ (túnel saliente)
Orange Pi (Nginx)


Tu Orange Pi solo hace conexiones salientes, nunca entrantes.

🧱 Paso 1: Instalar un servidor web ligero

Usa Nginx (consume muy poca RAM).
sudo apt update
sudo apt install nginx -y


Comprueba:
curl http://localhost

<img width="636" height="386" alt="image" src="https://github.com/user-attachments/assets/32206fc5-ca97-4144-9467-3c1de2eba379" />


La web está en:
/var/www/html/index.html



Desde otro equipo de tu red:
http://IP_orangepi

<img width="779" height="305" alt="image" src="https://github.com/user-attachments/assets/8cdd5aa7-a974-4d4e-a657-717543c12c0f" />

Ahora Vamos a crear un dominio GRATIS en DuckDNS 

Entra en 👉 https://www.duckdns.org

Inicia sesión (Google / GitHub)

En Domains, escribe un nombre, en mi caso "ebaclub"

Pulsa add domain

👉 Te quedará algo así:

ebaclub.duckdns.org

<img width="860" height="815" alt="image" src="https://github.com/user-attachments/assets/e38a7a6a-5b24-4cf6-885e-a03a544c912f" />


Crear tunnel cloudfare (web)

<img width="959" height="768" alt="image" src="https://github.com/user-attachments/assets/970eba9c-ef19-4ecd-a962-d44cdf96f3bf" />

PASO 1 – Instalar cloudflared en la orangepi (cliente del túnel)
Ejecuta:
cd /usr/local/bin
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm
mv cloudflared-linux-arm cloudflared
chmod +x cloudflared

Comando habilitar tunnel cloudfare

cloudflared tunnel login

<img width="649" height="89" alt="image" src="https://github.com/user-attachments/assets/c2668419-dd9b-4c52-9de1-d4dea28e9801" />

Entra en esa URL y aurotiza que se creee el tunnel

autorizar tunnel

<img width="947" height="927" alt="image" src="https://github.com/user-attachments/assets/4651c17e-4e6c-40c7-bbc9-40e73b39624f" />


SUCCESS

<img width="607" height="172" alt="image" src="https://github.com/user-attachments/assets/59ea0826-d2b2-4605-921c-c0989f875f64" />



listar tuneles de cloudfare

<img width="804" height="94" alt="image" src="https://github.com/user-attachments/assets/5cf048c5-3e65-4b69-b52c-2737625f35a4" />











