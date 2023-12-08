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

Atualize os pacotes da sua máquina

```bash
sudo apt update && apt upgrade -y
```

```bash
apt install docker-compose
```

```bash
mkdir flowise
```

```bash
cd flowise
```

```bash
nano docker-compose.yml
```

```bash
version: '3.1'

services:
    flowise:
        image: flowiseai/flowise
        restart: always
        environment:
            - PORT=${PORT}
            - FLOWISE_USERNAME=${FLOWISE_USERNAME}
            - FLOWISE_PASSWORD=${FLOWISE_PASSWORD}
            - DEBUG=${DEBUG}
            - DATABASE_PATH=${DATABASE_PATH}
            - DATABASE_TYPE=${DATABASE_TYPE}
            - DATABASE_PORT=${DATABASE_PORT}
            - DATABASE_HOST=${DATABASE_HOST}
            - DATABASE_NAME=${DATABASE_NAME}
            - DATABASE_USER=${DATABASE_USER}
            - DATABASE_PASSWORD=${DATABASE_PASSWORD}
            - APIKEY_PATH=${APIKEY_PATH}
            - SECRETKEY_PATH=${SECRETKEY_PATH}
            - FLOWISE_SECRETKEY_OVERWRITE=${FLOWISE_SECRETKEY_OVERWRITE}
            - LOG_LEVEL=${LOG_LEVEL}
            - LOG_PATH=${LOG_PATH}
        ports:
            - '${PORT}:${PORT}'
        volumes:
            - ~/.flowise:/root/.flowise
        command: /bin/sh -c "sleep 3; flowise start"
```

```bash
nano .env
```

```bash
PORT=3000
DATABASE_PATH=/root/.flowise
APIKEY_PATH=/root/.flowise
SECRETKEY_PATH=/root/.flowise
LOG_PATH=/root/.flowise/logs

NUMBER_OF_PROXIES= 1

DATABASE_TYPE=postgres
DATABASE_PORT=""
DATABASE_HOST=""
DATABASE_NAME="flowise"
DATABASE_USER=""
DATABASE_PASSWORD=""

FLOWISE_USERNAME=user
FLOWISE_PASSWORD=1234
FLOWISE_SECRETKEY_OVERWRITE=myencryptionkey
DEBUG=true
LOG_LEVEL=debug (error | warn | info | verbose | debug)
TOOL_FUNCTION_BUILTIN_DEP=crypto,fs
TOOL_FUNCTION_EXTERNAL_DEP=moment,lodash

LANGCHAIN_TRACING_V2=true
LANGCHAIN_ENDPOINT=https://api.smith.langchain.com
LANGCHAIN_API_KEY=your_api_key
LANGCHAIN_PROJECT=your_project
```

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

   proxy_pass http://127.0.0.1:3000;
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
