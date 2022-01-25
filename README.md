# getting-started-express

Make sure that you have node.js install on your computer.

1. Install express module(npm i express)

2. Setup-

const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(3000, () => {
  console.log("App is listening at http://localhost:3000")
})

3.  Install bodyparser(npm i body-parser) and directory setup

app.use(bodyParser.urlencoded({ extended: true }))

app.use(express.static(__dirname + '/public'))

4. Insert your html, css, js file in public directory inside your main application folder

5. Setup for html file rendering

const express = require('express')
const bodyParser = require("body-parser");

const app = express()

app.get('/', (req, res) => {
      res.render("/index.html");
})

app.listen(3000, () => {
  console.log(`App is listening at http://localhost:3000`)
})

6. Using EJS(Initialization)

const ejs = require('ejs')

app.set('view engine', 'ejs');

Variable - <%=variableName%>

Data Send -  res.render('index', {variableName: "Home"})

7. Using MYSQL  

const mysql = require('mysql');

const db = mysql.createConnection({
    host    :   'localhost',
    user    :   'root',
    password    :    '',
    database    :   'dataBaseName'
});

db.connect((err) => {
    if(err){
        throw err;
    }
    console.log('MySql Connected');
});

Creating Database-

  let sql = 'CREATE DATABASE dataBaseName';
  db.query(sql, (err, result) => {
      if(err) throw err;
      console.log(result);
      console.log('Database Created');
  });

Creating Table-

    let sql = 'CREATE TABLE tableName(id int AUTO_INCREMENT, NAME VARCHAR(255), EMAIL VARCHAR(255), PRIMARY KEY(id))';
    db.query(sql, (err, result) => {
        if(err) throw err;
        console.log(result);
        console.log('Table Created');
    });

app.post('/', (req, res) => {
    const name = req.body.name;
    const email = req.body.email;
    
    let data = {NAME: name, EMAIL: email};
    let sql = 'INSERT INTO tableName SET ?';
    let query = db.query(sql, data, (err, result) => {
        if(err) throw err;
        console.log(result);
        res.render('submit', {name:name});
    });
})

