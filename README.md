# webExpress
Skeleton for ExpressJS build

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

- Ubuntu
- NPM
- Internet


### Installing

- Initial Project
```
npm init
```
- Install ExpressJS
```
npm install express
```
- create index.js and input this code

```
'use strict'
var express = require('express')
,app = express()
,port = process.env.port || 3000
,bodyParser = require('body-parser');

app.use(bodyParser.urlencoded({extended : true}));
app.use(bodyParser.json);

app.listen(3000, () => {
console.log('App listening on port 3000!');
});
```

- Install nodemon
```
npm install nodemon
```

- Open pakage.json and add this code line inside the "scripts tag"
```
"start": "nodemon index.js"
```
and it will must be like this
```
{
  "name": "mywebsite",
  "version": "1.0.0",
  "description": "expressWeb",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "nodemon index.js"
  },
  "author": "dianagus96",
  "license": "ISC"
}
```
- make folder controllers, models, views
```
mkdir web/controllers web/models web/views
```
