N8N WITH EXTERNAL RUNNERS \n
This N8N is with external runner container for running Python in code node. Nginx-NPM ius to be used in front for reverse proxy and for SSL certificate.

Installation:

1) Pull Nginx-NPM from my Nginx-npm repo 
2) Docker Compose Nginx
    > docker compose up -d
4) Setup a Proxy Host
    *Domain
    * protocol: http
    * host: >Container name>
    * port: 5678
5) Get a certificate for n8n and bind it to host.      
6) 3)Pull N8N repo
7) Build runners image

    > docker compose build

8) Set up a runners token with Openssl
    > openssl rand -hex 32
    set it for .env variable N8N_RUNNERS_TOKEN= <token>
9) Docker Compose N8N
   



