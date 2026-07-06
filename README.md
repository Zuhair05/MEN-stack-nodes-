# MEN stack nodes

| CRUD Action | RESTful Action | HTTP Method | Definition |
| ----------- | -------------- | ----------- | ------------------------ |
|  | `new` | `GET` | Show a form to create a new item |
| Create | `create` | `POST` | Add a new item to the database |
| Read | `index` | `GET` | Show all items |
| Read | `show` | `GET` | Show one specific item |
| | `edit` | `GET` | Show a form to edit an existing item |
| Update | `update` | `PUT` | Save changes to an existing item |
| Delete | `delete` | `DELETE` | Remove an item from the database |

## SETUP

- creat a directory
- creat server file `touch server.js`
- creat a `.gitignore` file 
- initialize a node project with `npm init -y`
- install express `npm i express`

### Add `node_modules` to `.gitignore`

.gitignore
```bash
node_modules
```

### Write Server Boilerplate

server.js 
```js
const express = require('express')
const morgan = require('morgan');
const app = express()
app.use(morgan('dev'));



app.listen(3000, function() {
  console.log('Listening on port 3000')
})
```

Run the server with `nodemon server.js`

Navigate to `http://localhost:3000` to view our server.

use `ctrl+c` to stop the server in the terminal.

### Creating a Test Route 

```js
app.get('/test', function(req, res) {
  res.send('<h1>Test response.</h1>');
});
```
Navigate to `http://localhost:3000/test` to view our server.

### Using request parameter

```js
app.get('/:userId', function(req, res) {
    res.send(`<h1>userId: ${req.params.userId}</h1>`);
    console.log(req.params.userId)
  });
```
Navigate to `http://localhost:3000/2023` to view our server.

## Rendering EJS

- install ejs with `npm i ejs`
- creat a `views` directory
- creat an `.ejs` file like `home.ejs`
- add html boilerplate with `!`

  home.ejs
  ```html
  <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
</head>
<body>
    <h1>We are rendering an EJS page!</h1>
</body>
</html>
  ```
  - render `ejs` page using a controller like this one:

```js
app.get('/', (req, res) => {
  res.render('home.ejs');
})

```

