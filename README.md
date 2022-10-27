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
npm -D install jest nodemon jest-runner-groups
npm install express dotenv helmet morgan fs path

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
mkdir routes
mkdir __tests__
touch ./__tests__/unit.js
touch ./__tests__/component.js
touch ./__tests__/integration.js
```

## Starta WS Code

```bash
code .
```

## Helmet & Morgan

### app.js

```js
const express = require('express');
const app = express();
const morgan = require('morgan')
const helmet = require('helmet');

app.use(helmet());
app.use(morgan('tiny'));//combined


app.use((req, res, next) => {
    console.log('Den här körs vid varje anrop!')
    next();
})

module.exports = app;
```

## Helmet & Morgan to file

### app.js
```js
var express = require('express')
const app = express();
var fs = require('fs')
var morgan = require('morgan')
const helmet = require('helmet');
var path = require('path')

var accessLogStream = fs.createWriteStream(path.join(__dirname, 'access.log'), { flags: 'a' })

app.use(helmet());
app.use(morgan('combined', { stream: accessLogStream }))
app.use((req, res, next) => {
    console.log('Den här körs vid varje anrop!')
    next();
})

module.exports = app;
```

## server.js

```
const app = require('./app.js');
const PORT = process.env.PORT || 3000;

app.listen(PORT, () =>{
  console.log(`Server is listening to ${PORT}`);
}
```
