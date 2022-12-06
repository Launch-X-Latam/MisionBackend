# Introducción a Node.js

App.js
```JavaScript
const http = require('http'); // Cargando un módulo de Node.js
const url = require('url');

const rd = require('./modules/retrievedate') ; //Cargamos un módulo propio que esta en ./modules/retrievedate.js

http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/html'});
    //res.write("La fecha y hora es: "+ rd.RetrieveDate());
    const query = url.parse(req.url, true).query;
    const text = query.year + " " + query.month
    //res.end("Holaaaa Mundo!!!!");
    res.end(text);
}).listen(8080);
```

index.js
```JavaScript
const http = require('http');
const fs = require('fs');

http.createServer((req, res) => {
    fs.readFile('./html/demo.html', function(err, data) {
        res.writeHead(200, {'Content-Type': 'text/html'});
        res.write(data);
        return res.end();
    });
}).listen(3200);
```

/html/demo.html
````HTML
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8"/>
        <title>MI PÁGINA EN NODE</title>
    </head>
    <body>
        <h1>MIRA MAMÁ ESTOY PROGRAMANDO EN NODE</h1>
        <p>
            Estoy aprendiendo Node.js en vez de hacerme wey.
        </p>
    </body>
</html>

````

---

[**&#11176;** *Anterior* &#11007;](/03-Node.js/estructura-proyectos.md "Estructura de proyectos de Node.js") 
[Siguiente **&#129042;**](/03-Node.js/npm-package.md "NPM y Package JSON")

---

[*Volver* **&ldca;**](/README.md "Menu principal") 
[*Subir* **&#11165;**](# "Ir al título")