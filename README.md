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

Atualzie os pacotes da sua VM

```bash
sudo apt update && apt upgrade -y
```

### Instale o Node V20x.

```bash
sudo apt-get install -y ca-certificates curl gnupg
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
```

`` bash
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

### inicie o flow com usuário e senha
```bash
npx flowise start & --FLOWISE_USERNAME=user --FLOWISE_PASSWORD=1234
```

### Instalação do Nginx proxy reverso

```bash
sudo apt install nginx
```

``bash
sudo nano /etc/nginx/sites-available/flowise
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
