# password checker

https://scribehow.com/shared/Create_Docker_Container_with_Port_Mapping_and_Commands__lIFZJ6H_SnaVIpwtIlKNlg
image in docker hub : **ahmedfnx/pass-check**

---

# certificate generation
https://github.com/semikolan-co/Certificate-Generator

https://scribehow.com/shared/Create_Docker_Container_with_Port_Mapping_for_Certifications-gen__TVcBdYNxQsKxBsS-k_Eiyg
image in docker hub : **ahmedfnx/fnx-cert-gen**

---

# https://rxresu.me

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


# one time sescret sharing app :

Step 1 & 2. step1
![220198712-7d379d69-3fdb-430a-93f6-c02c0d6b4ae9](https://github.com/anything-good/fnx/assets/90029363/20664846-04f7-4b14-976a-1abeca41e870)

Step 3. step 2
![220198843-8be34f58-f7dd-465d-b59a-7e9b4764ffc0](https://github.com/anything-good/fnx/assets/90029363/4dbd6c9a-b290-4764-92df-b847ec2d3c5f)

Press Deploy the stack to deploy.

---

https://gethomepage.dev/latest/installation/docker/
  
https://github.com/738/awesome-url-shortener

https://alf.io/

https://particify.de/en/

https://shlink.io/

https://www.wiz.cn/docker

https://akaunting.com/

https://affine.pro/


https://github.com/Briuor/wbm?tab=readme-ov-file
