# getting-started-express

Make sure that you have node.js install on your computer.

1. Install express module(npm i express)

2. Setup

const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(3000, () => {
  console.log(`App is listening at http://localhost:${port}`)
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
  console.log(`App is listening at http://localhost:${port}`)
})
