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



### jitsi meet 

https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-docker

docker compose :
```
version: '3'

services:
    # Frontend
    jitsi-meet:
        image: jitsi/web:web-1.0.7874-1@sha256:5f6f4b646fb2c57670bf4463905d5b7fd37538adc4eba108c4afff25f73537db
        restart: ${RESTART_POLICY}
        volumes:
            - ${CONFIG}/web:/config:Z
            - ${CONFIG}/web/letsencrypt:/etc/letsencrypt:Z
            - ${CONFIG}/transcripts:/usr/share/jitsi-meet/transcripts:Z
        environment:
            - ENABLE_AUTH
            - ENABLE_GUESTS
            - ENABLE_LETSENCRYPT
            - ENABLE_HTTP_REDIRECT
            - ENABLE_TRANSCRIPTIONS
            - DISABLE_HTTPS
            - JICOFO_AUTH_USER
            - LETSENCRYPT_DOMAIN
            - LETSENCRYPT_EMAIL
            - PUBLIC_URL
            - XMPP_DOMAIN
            - XMPP_AUTH_DOMAIN
            - XMPP_BOSH_URL_BASE
            - XMPP_GUEST_DOMAIN
            - XMPP_MUC_DOMAIN
            - XMPP_RECORDER_DOMAIN
            - ETHERPAD_URL_BASE
            - ETHERPAD_PUBLIC_URL
            - TZ
            - JIBRI_BREWERY_MUC
            - JIBRI_PENDING_TIMEOUT
            - JIBRI_XMPP_USER
            - JIBRI_XMPP_PASSWORD
            - JIBRI_RECORDER_USER
            - JIBRI_RECORDER_PASSWORD
            - ENABLE_RECORDING
        
        ports:
            - '${HTTP_PORT}:80'
            - '${HTTPS_PORT}:443'
        networks:
            proxy:
            meet.jitsi:
                aliases:
                    - ${XMPP_DOMAIN}
                    
        # labels:
        #     - "traefik.enable=true"
        #     - "traefik.docker.network=proxy"
        #     ## HTTP Routers
        #     - "traefik.http.routers.jitsi-meet.entrypoints=https"
        #     - "traefik.http.routers.jitsi-meet.rule=Host(`$XMPP_DOMAIN`)"
        #     #HTTPS Routes
        #     - "traefik.http.routers.jitsi-meet-secure.rule=Host(`jitsi-meet.fnx.tools`)"

        #     ## Middlewares
        #     - "traefik.http.routers.jitsi-meet.middlewares=chain-jitsi-auth@file"
        #     ## HTTP Services
        #     - "traefik.http.services.jitsi-meet.loadbalancer.server.port=80"
        labels:
          - "traefik.enable=true"
          - "traefik.http.routers.jitsi-meet.entrypoints=http"
          - "traefik.http.routers.jitsi-meet.rule=Host(`jitsi-meet.fnx.tools`)"
          - "traefik.http.middlewares.jitsi-meet-https-redirect.redirectscheme.scheme=https"
          - "traefik.http.routers.jitsi-meet.middlewares=jitsi-meet-https-redirect"
          - "traefik.http.routers.jitsi-meet-secure.entrypoints=https"
          - "traefik.http.routers.jitsi-meet-secure.rule=Host(`jitsi-meet.fnx.tools`)"
          - "traefik.http.routers.jitsi-meet-secure.tls=true"
          - "traefik.http.routers.jitsi-meet-secure.service=jitsi-meet"
          - "traefik.http.services.jitsi-meet.loadbalancer.server.port=80"
          - "traefik.docker.network=proxy"
    

    # XMPP server
    prosody:
        image: jitsi/prosody:prosody-0.12.4@sha256:3992343768afb32028a1999c337f12b9f413bbd531b33669d0e3916fd1d29d0a
        restart: ${RESTART_POLICY}
        expose:
            - '5222'
            - '5347'
            - '5280'
        volumes:
            - ${CONFIG}/prosody/config:/config:Z
            - ${CONFIG}/prosody/prosody-plugins-custom:/prosody-plugins-custom:Z

        labels:
            - "traefik.enable=true"
            ## HTTP Routers
            - "traefik.http.routers.jitsi-prosody-ws.entrypoints=https"
            - "traefik.http.routers.jitsi-prosody-ws.rule=Host(`$XMPP_DOMAIN`) && Path(`/xmpp-websocket`)"
            ## Middlewares
            - "traefik.http.routers.jitsi-prosody-ws.middlewares=chain-jitsi-auth@file"
            ## HTTP Services
            - "traefik.http.services.jitsi-prosody-ws.loadbalancer.server.port=5280"

        
        environment:
            - AUTH_TYPE
            - ENABLE_AUTH
            - ENABLE_GUESTS
            - GLOBAL_MODULES
            - GLOBAL_CONFIG
            - LDAP_URL
            - LDAP_BASE
            - LDAP_BINDDN
            - LDAP_BINDPW
            - LDAP_FILTER
            - LDAP_AUTH_METHOD
            - LDAP_VERSION
            - LDAP_USE_TLS
            - LDAP_TLS_CIPHERS
            - LDAP_TLS_CHECK_PEER
            - LDAP_TLS_CACERT_FILE
            - LDAP_TLS_CACERT_DIR
            - LDAP_START_TLS
            - XMPP_DOMAIN
            - XMPP_AUTH_DOMAIN
            - XMPP_GUEST_DOMAIN
            - XMPP_MUC_DOMAIN
            - XMPP_INTERNAL_MUC_DOMAIN
            - XMPP_MODULES
            - XMPP_MUC_MODULES
            - XMPP_INTERNAL_MUC_MODULES
            - XMPP_RECORDER_DOMAIN
            - JICOFO_COMPONENT_SECRET
            - JICOFO_AUTH_USER
            - JICOFO_AUTH_PASSWORD
            - JVB_AUTH_USER
            - JVB_AUTH_PASSWORD
            - JIGASI_XMPP_USER
            - JIGASI_XMPP_PASSWORD
            - JIBRI_XMPP_USER
            - JIBRI_XMPP_PASSWORD
            - JIBRI_RECORDER_USER
            - JIBRI_RECORDER_PASSWORD
            - JWT_APP_ID
            - JWT_APP_SECRET
            - JWT_ACCEPTED_ISSUERS
            - JWT_ACCEPTED_AUDIENCES
            - JWT_ASAP_KEYSERVER
            - JWT_ALLOW_EMPTY
            - JWT_AUTH_TYPE
            - JWT_TOKEN_AUTH_MODULE
            - LOG_LEVEL
            - TZ
        networks:
            meet.jitsi:
                aliases:
                    - ${XMPP_SERVER}

    # Focus component
    jicofo:
        image: jitsi/jicofo:jicofo-1.0-1075-1@sha256:633679bb7f7aaf0217228f1800269cca23bce87b127d259dfa2743a412e2a670
        restart: ${RESTART_POLICY}
        volumes:
            - ${CONFIG}/jicofo:/config:Z
        environment:
            - AUTH_TYPE
            - ENABLE_AUTH
            - XMPP_DOMAIN
            - XMPP_AUTH_DOMAIN
            - XMPP_INTERNAL_MUC_DOMAIN
            - XMPP_SERVER
            - JICOFO_COMPONENT_SECRET
            - JICOFO_AUTH_USER
            - JICOFO_AUTH_PASSWORD
            - JICOFO_RESERVATION_REST_BASE_URL
            - JVB_BREWERY_MUC
            - JIGASI_BREWERY_MUC
            - JIBRI_BREWERY_MUC
            - JIGASI_SIP_URI
            - JIBRI_PENDING_TIMEOUT
            - TZ
        depends_on:
            - prosody
        networks:
            meet.jitsi:

    # Video bridge
    jvb:
        image: jitsi/jvb:jvb-2.3-92-g64f9f34f-1@sha256:869e85bf88f75a39a83ed78c8cce7969d83f8dedf860f01e4c46f01f6f92fb55
        restart: ${RESTART_POLICY}
        ports:
            - "${JVB_PORT}:${JVB_PORT}"
            - "${JVB_TCP_MAPPED_PORT}:${JVB_TCP_PORT}"
        
        labels:
            - "traefik.enable=true"
            ## HTTP Routers
            - "traefik.http.routers.jitsi-colibri-ws.entrypoints=https"
            - "traefik.http.routers.jitsi-colibri-ws.rule=Host(`$XMPP_DOMAIN`) && PathPrefix(`/colibri-ws`)"
            ## Middlewares
            - "traefik.http.routers.jitsi-colibri-ws.middlewares=chain-jitsi-auth@file"
            ## HTTP Services
            - "traefik.http.services.jitsi-colibri-ws.loadbalancer.server.port=9090"
        volumes:
            - ${CONFIG}/jvb:/config:Z
        environment:
            - DOCKER_HOST_ADDRESS
            - XMPP_AUTH_DOMAIN
            - XMPP_INTERNAL_MUC_DOMAIN
            - XMPP_SERVER
            - JVB_AUTH_USER
            - JVB_AUTH_PASSWORD
            - JVB_BREWERY_MUC
            - JVB_PORT
            - JVB_TCP_HARVESTER_DISABLED
            - JVB_TCP_PORT
            - JVB_STUN_SERVERS
            - JVB_ENABLE_APIS
            - COLIBRI_REST_ENABLED
            - SHUTDOWN_REST_ENABLED
            - TZ
        depends_on:
            - prosody
        networks:
            meet.jitsi:

# Custom network so all services can communicate using a FQDN
networks:
    meet.jitsi:
    # traefik: change the following line to your external docker network 
    proxy:
        external: true

```

.env :
```
# .env

# Basic configuration options
CONFIG=~/.jitsi-meet-cfg
HTTP_PORT=8084
HTTPS_PORT=8443
TZ=UTC
XMPP_DOMAIN=jitsi-meet.fnx.tools
PUBLIC_URL=https://jitsi-meet.fnx.tools
LETSENCRYPT_DOMAIN=https://jitsi-meet.fnx.tools
JVB_TCP_PORT=9090
JVB_PORT=7790
JVB_TCP_MAPPED_PORT=7090
DOCKER_HOST_ADDRESS=84.235.245.241
RESTART_POLICY=always

# Authentication configuration
ENABLE_AUTH=1
ENABLE_GUESTS=1
AUTH_TYPE=internal

# Security
JICOFO_AUTH_PASSWORD=08b93c13f397b02c3f5e22676a1e3846
JVB_AUTH_PASSWORD=2cb9005896b81d9f0857b86162486644
JIGASI_XMPP_PASSWORD=5cb436ab841f5ef0503c4620c5fedf47
JIBRI_RECORDER_PASSWORD=8f24152b343c05df0acb39643e8ee59c
JIBRI_XMPP_PASSWORD=b872dbe76f4f431f5e6cf9dfdf41bc28

```
