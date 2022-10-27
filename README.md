# edu-secure-server-js
A simple secure server.

## Gå till ditt projekt
```bash
cd ~
cd ws
mkdir secure-server-js
cd secure-server-js
```

## Preppa Node

```bash
npm -D install jest nodemon
npm install dotenv express 

npm install express --save
npm install healthcheck --save
npm install dotenv --save
npm install cors --save
npm install jsonwebtoken --save
npm install nodemon --save-dev
npm install jest --save-dev
npm install jest-runner-groups --save-dev
#Inget mellanslag runt =, för då funkar inte set commandot
npm pkg set main="server.js"
npm pkg set scripts.dev="nodemon server.js" 
npm pkg set scripts.test="jest  --group=-component --group=-integration"
npm pkg set scripts.componenttest="jest  --group=component"
npm pkg set scripts.integrationtest="jest  --group=integration"


```

## Preppa filer

```bash
touch .env
touch app.js
touch server.js
touch .env
mkdir routes
touch routes/healthcheck.js 
touch routes/user.js
mkdir __tests__
touch ./__tests__/unit.js
touch ./__tests__/component.js
touch ./__tests__/integration.js
```

## Starta WS Code

```bash
code .
```
