# **N8N WITH EXTERNAL RUNNERS**

This is Docker N8N with an external runner container for running Python in the Code node.  
Nginx‑NPM is to be used in front for reverse proxy and for SSL certificate.

---
## **Prerequisites**
Docker + docker compose installed


## **Installation**
1) Create n8n-network 
```bash
docker network create n8n-network
```
2) Pull Nginx‑NPM from my nginx‑npm repo.

3) setup MariaDB credentials

Set it in `.env` as:  
```
MYSQL_ROOT_PASSWSORD=<password>
MYSQL_PASSWORD=<password>
```
4) Docker Compose Nginx  
```bash
docker compose up -d
```

> ⚠️ **Warning:**  
> Ensure you run this command **inside the directory that contains the Nginx‑NPM `docker-compose.yml` file**.  
> Running it in another folder will either fail or launch the wrong stack.

5) Setup a Proxy Host  
- Domain  
- Protocol: **http**  
- Host: `<Container name>`  
- Port: **5678**

6) Get a certificate for n8n and bind it to the host.

7) Pull N8N repo.

8) Build runners image  
```bash
docker compose build
```

9) Set up a runners token with OpenSSL  
```bash
openssl rand -hex 32
```

Set it in `.env` as:  
```
N8N_RUNNERS_TOKEN=<token>
```
10) Setup Prostgres database password
   
Set it in `.env` as:  
```
POSTGRES_PASSWORD=<password>
```
  
11) Docker Compose N8N  
```bash
docker compose up -d
```
