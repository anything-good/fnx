## password checker

https://scribehow.com/shared/Create_Docker_Container_with_Port_Mapping_and_Commands__lIFZJ6H_SnaVIpwtIlKNlg
image in docker hub : ahmedfnx/pass-check

---

## certificate generation
https://github.com/semikolan-co/Certificate-Generator

https://scribehow.com/shared/Create_Docker_Container_with_Port_Mapping_for_Certifications-gen__TVcBdYNxQsKxBsS-k_Eiyg
image in docker hub : ahmedfnx/fnx-cert-gen

---

## https://rxresu.me

documentations with images: 
https://scribehow.com/shared/Create_Stack_resume_via_Web_Interface__JSkZB87KRaWofTAXtUnyvA

create a new portainer stack with the following file (use docker compose) :
```
version: "3.8"

services:
  postgres:
    image: postgres:alpine
    restart: always
    ports:
      - 5432:5432
    volumes:
      - pgdata:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      start_period: 15s
      interval: 30s
      timeout: 30s
      retries: 3
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres

  server:
    image: amruthpillai/reactive-resume:server-latest
    restart: always
    ports:
      - 3100:3100
    depends_on:
      - postgres
    environment:
      - PUBLIC_URL=http://localhost:3000
      - PUBLIC_SERVER_URL=http://localhost:3100
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
      - SECRET_KEY=change-me-to-something-secure
      - POSTGRES_HOST=postgres
      - POSTGRES_PORT=5432
      - JWT_SECRET=change-me-to-something-secure
      - JWT_EXPIRY_TIME=604800
      
  client:
    image: amruthpillai/reactive-resume:client-latest
    restart: always
    ports:
      - 3000:3000
    depends_on:
      - server
    environment:
      - PUBLIC_URL=http://localhost:3000
      - PUBLIC_SERVER_URL=http://localhost:3100
      
volumes:
  pgdata:

```

## one time sescret sharing app :

Step 1 & 2. step1
![220198712-7d379d69-3fdb-430a-93f6-c02c0d6b4ae9](https://github.com/anything-good/fnx/assets/90029363/20664846-04f7-4b14-976a-1abeca41e870)

Step 3. step 2
![220198843-8be34f58-f7dd-465d-b59a-7e9b4764ffc0](https://github.com/anything-good/fnx/assets/90029363/4dbd6c9a-b290-4764-92df-b847ec2d3c5f)


* https://github.com/rpgeeganage/ots-share-app.git

* refs/heads/main

* docker-compose.bundle.yml

Press Deploy the stack to deploy.

---

## https://gethomepage.dev/latest/installation/docker/
```
version: "3.3"
services:
  homepage:
    image: ghcr.io/gethomepage/homepage:latest
    container_name: homepage
    ports:
      - 30:3000
    volumes:
      - /path/to/config:/app/config # Make sure your local config directory exists
      - /var/run/docker.sock:/var/run/docker.sock # (optional) For docker integrations

```

## Cyper Chef  https://github.com/gchq/CyberChef:

image link : not in dockerhub : ghcr.io/gchq/cyberchef:latest
```
version: '3.8'

services:
  cyberchef:
    image: ghcr.io/gchq/cyberchef:latest
    ports:
      - "8580:80"
```

---

## https://github.com/recurser/string-is : 

docker image name : daveperrett/string-is

---


## openproject : 
First, you must clone the  [openproject-deploy](https://github.com/opf/openproject-deploy/tree/stable/13/compose)  repository:

```
git clone https://github.com/opf/openproject-deploy --depth=1 --branch=stable/13 openproject
```
Then, change into the compose folder, this folder will be the location where you enter all following commands:
```
cd openproject/compose
```
Make sure you are using the latest version of the Docker images:
```
docker-compose pull
Launch the containers:
OPENPROJECT_HTTPS=false docker-compose up -d
```

After a while, OpenProject should be up and running on http://localhost:8080. 
The default username and password is login: admin, and password: admin. You need to explicitly disable HTTPS mode on startup as OpenProject assumes it’s running behind HTTPS in production by default.


 ## [https://www.wiz.cn/docker](https://www.wiz.cn/docker)  :

1.  Run this command in Terminal to create a data folder
```
cd ~
mkdir wizdata
```

Create a folder wizdata for preserving all the data of WizNote Server. Please backup this folder regularly. If you want to use NAS or private cloud as data storage, please contact us.


2.  Run the command below to run the docker container

```
docker run --name wiz -it -d -v ~/wizdata:/wiz/storage -v /etc/localtime:/etc/localtime -p 80:80 -p 9269:9269/udp wiznote/wizserver
```
## class quiz maker
follow the instructions in the link :
https://classquiz.de/docs/self-host


## uptime-kuma

```
version: '3.3'
services:
  uptime-kuma:
    container_name: uptime-kuma
    image: louislam/uptime-kuma:1
    ports:
      - "3001:3001"
    volumes:
      - uptime-kuma:/app/data
    restart: always

volumes:
  uptime-kuma:

```

## Excalidraw

```
version: '3.8'

services:
  excalidraw:
    image: excalidraw/excalidraw:latest
    ports:
      - "8670:80"
    restart: unless-stopped

```

## neonlink (**https://github.com/AlexSciFier/neonlink**)

you shall use docker compose :
```
version: "3.8"

services:
  neonlink:
    image: alexscifier/neonlink
    container_name: neonlink
    # user: 1000:1000 # optional
    volumes:
      - ./data:/app/data
      - ./background:/app/public/static/media/background
    restart: unless-stopped
    environment:
      FASTIFY_PLUGIN_TIMEOUT: 0 # optional: change to 0 if AVV_ERR_READY TIMEOUT error is occured
    ports:
      - "8010:3333"
```


## password-pusher
```
version: '3.8'

services:
  pwpush-ephemeral:
    image: pglombardo/pwpush-ephemeral:release
    ports:
      - "5770:5100"
    restart: unless-stopped
```

## filegator (file hosting server):

* image name :```filegator/filegator``` .
* port to be published 8080 .
*login as admin , pasword: admin123 .

## memories app (memos)

```
version: "3.0"
services:
  memos:
    image: neosmemo/memos:latest
    container_name: memos
    volumes:
      - ~/.memos/:/var/opt/memos
    ports:
      - 5230:5230
```

## leantime :

```
git clone https://github.com/Leantime/docker-leantime.git
cd docker-leantime
cp sample.env .env
nano .env    # Change the secrets for security
docker-compose up -d
```


## screego :

```
version: "3.7"

services:
  screego:
    image: ghcr.io/screego/server:arm64-1
    ports:
      - "5050:5050"
      - "3478:3478"
      - "50000-50200:50000-50200/udp"
    environment:
      SCREEGO_EXTERNAL_IP: "84.235.245.241"
      SCREEGO_TURN_PORT_RANGE: "50000:50200"
      
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.screego.entrypoints=http"
      - "traefik.http.routers.screego.rule=Host(`screego.fnx.tools`)"
      - "traefik.http.middlewares.screego-https-redirect.redirectscheme.scheme=https"
      - "traefik.http.routers.screego.middlewares=screego-https-redirect"
      - "traefik.http.routers.screego-secure.entrypoints=https"
      - "traefik.http.routers.screego-secure.rule=Host(`screego.fnx.tools`)"
      - "traefik.http.routers.screego-secure.tls=true"
      - "traefik.http.routers.screego-secure.service=screego"
      - "traefik.http.services.screego.loadbalancer.server.port=3478"
      - "traefik.docker.network=proxy"


networks:
  proxy:
    external: true


```
