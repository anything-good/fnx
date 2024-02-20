## password checker

https://scribehow.com/shared/Create_Docker_Container_with_Port_Mapping_and_Commands__lIFZJ6H_SnaVIpwtIlKNlg
image in docker hub : **ahmedfnx/pass-check**

---

## certificate generation
https://github.com/semikolan-co/Certificate-Generator

https://scribehow.com/shared/Create_Docker_Container_with_Port_Mapping_for_Certifications-gen__TVcBdYNxQsKxBsS-k_Eiyg
image in docker hub : **ahmedfnx/fnx-cert-gen**

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
      - 3000:3000
    volumes:
      - /path/to/config:/app/config # Make sure your local config directory exists
      - /var/run/docker.sock:/var/run/docker.sock # (optional) For docker integrations
```

## Cyper Chef  https://github.com/gchq/CyberChef:

image link : **not in dockerhub : ghcr.io/gchq/cyberchef:latest**

```
version: '3.8'

services:
  cyberchef:
    image: ghcr.io/gchq/cyberchef:latest
    ports:
      - "8080:80"
```

---

## https://github.com/recurser/string-is : 

docker image name : daveperrett/string-is

---

## penpot designtool :

docker compose file link (it is quit a long one) :
```https://raw.githubusercontent.com/penpot/penpot/main/docker/images/docker-compose.yaml```

---

## workout and nutrition web app :

docker compose file link (also a long file) :
```https://github.com/wger-project/docker/raw/master/docker-compose.yml```

---
## 2FAuth : 
docker compose file link (also a long file) :
```https://github.com/Bubka/2FAuth/raw/master/docker/docker-compose.yml```

---


## openproject : 
docker compose file link (also a long file) :
```https://github.com/opf/openproject-deploy/raw/stable/13/compose/docker-compose.yml```

---

## https://alf.io (ticket reservation system):
docker compose file link  :
```https://github.com/alfio-event/alf.io/raw/main/docker-compose.yml```

---


## intractive quiz maker : 
docker compose file link  :
```https://github.com/mawoka-myblock/ClassQuiz/raw/master/docker-compose.yml```

---

## https://www.wiz.cn/docker :
docker compose file link  :

```https://github.com/containrrr/watchtower/raw/main/docker-compose.yml```

---

https://akaunting.com/ :

docker image name : ```akaunting/akaunting```
just add the above container into docker .

---


https://affine.pro/

```
version: '3.8'

services:
  affine:
    image: ghcr.io/toeverything/affine-self-hosted:latest
    container_name: affine
    ports:
      - "3000:3000"

```


https://github.com/Briuor/wbm?tab=readme-ov-file
