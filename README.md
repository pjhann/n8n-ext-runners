# **N8N WITH EXTERNAL RUNNERS**

This N8N is with an external runner container for running Python in the Code node.  
Nginx‑NPM is to be used in front for reverse proxy and for SSL certificate.

---
## **Prerequisites**
Docker + docker compose installed
```bash
docker network create n8n-network
```

## **Installation**
1) Create n8n-network 


1) Pull Nginx‑NPM from my nginx‑npm repo.
2) setup MariaDB credentials to .env

3) Docker Compose Nginx  
```bash
docker compose up -d
```

> ⚠️ **Warning:**  
> Ensure you run this command **inside the directory that contains the Nginx‑NPM `docker-compose.yml` file**.  
> Running it in another folder will either fail or launch the wrong stack.

4) Setup a Proxy Host  
- Domain  
- Protocol: **http**  
- Host: `<Container name>`  
- Port: **5678**

5) Get a certificate for n8n and bind it to the host.

6) Pull N8N repo.

7) Build runners image  
```bash
docker compose build
```

8) Set up a runners token with OpenSSL  
```bash
openssl rand -hex 32
```

Set it in `.env` as:  
```
N8N_RUNNERS_TOKEN=<token>
```
9) Setup Prostgres database password
   
  Set it in `.env` as:  
```
POSTGRES_PASSWORD=<password>
```
  
11) Docker Compose N8N  
```bash
docker compose up -d
```
