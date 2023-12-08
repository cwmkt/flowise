<p align="center">
<img src="https://cwmkt.com.br/wp-content/uploads/2023/08/logo-github-cwmkt.svg" alt="DispZap Whats Marketing" width="240" />
<p align="center">Seja bem-vindo ao Guia de Instalação do Flowise 🚀</p>
</p>
  
<p align="center">
<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
<span>Grupo WhatsaAPP: </span>
<a href="https://chat.whatsapp.com/H725cLemtTY5iAW6lFScPF" target="_blank">Grupo</a>
</p>

<hr />
<hr />

 
### Manual de Instalação Flowise

Atualize os pacotes da sua máuquina

```bash
sudo apt update && apt upgrade -y
```

### Instale o Node V20x.

```bash
sudo apt-get install -y ca-certificates curl gnupg
```

```bash
sudo mkdir -p /etc/apt/keyrings
```

```bash
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
```

```bash
NODE_MAJOR=20
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
```

```bash
sudo apt-get update
sudo apt-get install nodejs -y
```

### Instalação do Flowise

```bash
npm install -g flowise
```

### Inicie o Flowise com usuário e senha
```bash
FLOWISE_USERNAME=user FLOWISE_PASSWORD=1234 npx flowise start &
```

💡Substitua `user` pelo nome de usuário desejado<br>
💡Substitua `1234` por uma senha segura.

### Instalação do Nginx proxy reverso

```bash
sudo apt install nginx
```

```bash
sudo nano /etc/nginx/sites-available/flowise
```

```bash
server {
  server_name flowise.dominio.com.br;
  
  underscores_in_headers on;

  location / {

   proxy_pass http://127.0.0.1:5678;
   proxy_pass_header Authorization;
   proxy_set_header Upgrade $http_upgrade;
   proxy_set_header Connection "upgrade";
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-Proto $scheme;
   proxy_set_header X-Forwarded-Ssl on; # Optional
   proxy_set_header X-Real-IP $remote_addr;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   proxy_http_version 1.1;
   proxy_set_header Connection "";
   proxy_buffering off;
   client_max_body_size 0;
   proxy_read_timeout 36000s;
   proxy_redirect off;
  }
  add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
  ssl_protocols TLSv1.2 TLSv1.3;
} 
  ```

```bash
sudo ln -s /etc/nginx/sites-available/flowise /etc/nginx/sites-enabled
```

```bash
sudo apt-get install snapd
```

```bash 
sudo snap install notes
```

```bash
sudo snap install --classic certbot
```

```bash  
sudo certbot --nginx
```

```bash  
sudo service nginx restart
```

### Pronto ✅ Instalação concluída
