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
touch index.js
```
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
- make folder controllers, models, views, routes
```
mkdir -p web/controllers web/models web/views web/routes
```
- make file webRoutes.js inside web/routes
```
touch web/routes/webRoutes.js
```
- open web/routes/webRoutes.js and insert this code
```
'use strict';
module.exports = function(app){
    var web  = require('../controllers/webController');
    
    app.route('/')
        .get(web.login)
        .post(web.login);
        
};
```
- make file webController.js inside web/controllers
```
touch web/controllers/webController.js
```
- open web/controllers/webController.js and insert this code
```
'use strict'
exports.login = function(req, res){
    if(req.method == 'GET'){
        res.render("index");
    }else{
        res.redirect("/home");
    }
}

exports.home = function(req, res){
    res.status(200).render('home');
}
```
- open index.js and we link the routes to the project
```
routes = require('./web/routes/webRoutes')
routes(app);
```
and it will must be this
```
'use strict'
var express = require('express')
    ,app = express()
    ,port = process.env.port || 3000
    ,bodyParser = require('body-parser')
    ,routes = require('./web/routes/webRoutes');

app.use(bodyParser.urlencoded({extended : true}));
app.use(bodyParser.json);

routes(app);

app.listen(port, () => {
    console.log('App listening on port 3000!');
});

```
