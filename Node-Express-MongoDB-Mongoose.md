# NodeJs Bootcamp

Created: May 08, 2020 8:16 PM
Reviewed: No

Node para trabajar asincronicamente, utiliza callbacks(err, data) -mas comun- y promises (E6 es async y await)

-Cargar un file

const fs = require("fs");

const textIn= fs.readFileSync("./path")

-Leer un file

```jsx
fs.readFile("./path", "utf-8!, (err,data)⇒{
	console.log(data)
})
```

-Web server

```jsx
const http = require("http");
//1 Crear el server
const server = http.createServer(req, res)=>{
	res.send("Hello there")
}
//res es la respuesta que enviamos
//escuchar
server.listen(8000, ()=>{
	console.log("Listening to request")
}
```

-Routing—> se usa express

```jsx
//sin express
const pathName = req.url.
if(pathName === "/"){
	res.send("hii")
}
```

-Importar modulos

```jsx
module.exports = "anonymous function"
//para importar
const importFunction = require("./path")
 o

module.exports = Calculator;
const C = require("./modCalculator")
```

-Para empezar un projecto:

```jsx
//terminal
npm init //inicializar el .json
```

-El paquete "slugify" permite ponerle un nombre a la ultima parte de la ruta de un pagina, en vez que solo aparecezca lo que seria la query ?=id1. Se llama slug

```jsx
npm slugify --save
const slugify = require("slugify")

const slugs = dataObj.map(el => sllugify(el.productName), {lower: true})

```

Que sucede cuando accedemos a una web:

-El cliente(el browser) envia un request al server(servidor) el cual le devuelve una respuesta ⇒ Cliente-server-arquitecture // Request-response model.

Cada url tiene:

https://www.google.com/maps/

Protocolo:https

Nombre de dominio: www.[google.com](http://google.com), el cual en realidad no es el dominio, sino un nombre "amigable" para nosotros- El DNS(domain name server) es el que se encarga de matchear este nombre con los numeros que forman el verdadero dominio(Direccion IP).

Recurso al que querermos acceder: /maps 

Cuando se tiene el IP nombre, se realiza la coneccion a travez de la IP. 

El transpaso se hace a travez de socket connection, que envia la data en forma de apquetes pequeños para que llegue mas rapido

Se hace un request del tipo HTTP (hiper text transfer protocol), comunication protocol que permite dos puertos comunicarse (cliente y servidor)

El request se compone por:

-start line: HTTP method (GET, POST, DELETE) seguido del request targer (path, router) y el HTTP version.

-HTTP request header: que contiene informacion propia del request: el host, user-agent (mozilla, explorer), el lenguage, etc.

-Body: solo para los POST request, que es la info que se mandar al server

HTTPS: es encrypted

Luego el server envia de la misma forma un HTTP Response: 200 Ok ⇒start line, 404 no. Lo que llega: index.html, JS, CSS, IMG y hace el request por cada file

//////////////////////////

express framework.

```jsx
npm install express --save
const express = require("express")
const app = express();

//Ayuda a definir routes y realizar request 

app.get("/", (req, res)=>{
	res.send("hi, there")
});

app.listen(3000, ()=>{
 console.log("server is running");
}

//Se debe poner al final, el ordenamiento de las routes importan
app.get("*", (req,res)=>{
 res.send("This page does not exist!")
}
//route parameters
app.get("/r/:subredditName/:id", (req,res)=>{
	res.send("");
	console.log(req.params); //un param es cada :XXX /
}
```

```jsx
npm init
npm install express --save

const express = require("express")
const app = express()

app.get("/", (req, res) =>{
	res.send("Hi there, welcome to my assigment!")
});

app.get("/speak/:animal", (req, res)=>{
	const animal = req.params.animal;
	const soundPig = "oink";
	const soundCow = "Moo";
	const soundDog = "Woof Woof";

	if(animal === "pig"){
	res.send(`The pig says ${soundPig}`)
	
});

app.listen(3000, ()=>{
	console.log("server is running");
}
```

Para renderizar algo en una pagina de acuerdo al route:

```jsx
//primero se necesita instalar ejs

npm install ejs --save 
//ejs significa embeded javascript, permite cargar JS dentro de un html
app.get("/youfellinlovewith/:name", (req,res)=>{
	const name = req.params.name;
	res.render("love.ejs", {name : name} ); 
//1.Para que express encuentre el archivo .ejs e debe guardar dentro de un directorio llamado "views"
//2.En el .ejs utilizare la const name, para eso debo "mandarla" de alguna forma, lo hago
//con {name : name) ==> {nombre que elijo para pasar: nombre de la variable} generalmente se usa el mismo
})

//creo un file ejs llamado love.ejs, pero antes debo pasar 
<h1>YOU FELL IN LOVE WITH: <%= name %> <h1>
//para embeber js se usa <%= %> y adentro js
//hay dos tipos de caracteres:
<%= //inserta lo que escribo despues en el html
<% //solo realiza la logica detras, se usa en condicionales y loops

<% if(name === "claudia") { %>
	<h1>You are the best </h1>
<% } %>

```

De otra manera se hacer con "partials"  para crear templates que puedan ser usados en cada route.

```jsx
//creamos un directorio llamado "public" para incluir css
<link href="app.css" rel="stylesheet">
//para eso hay que indicarselo a express

//Entonces, en app.js

app.use(express.static("public")); //que express siva el contenido desde la carpeta public

//Se crea un header.ejs con el template
// y ahi se incluye el stylesheet
//Luego en cada route se agrega:
<%- include("partials/header") %>
```

Para evitar unar un archivo con .ejs

```jsx
app.set("view engine", "ejs");
//con esto se puede escribir solo el nombre del archivo 
```

POST request: se debe instalar body parser, para poder leer lo que el objeto req.body contiene

```jsx
const bodyParser = require("body-parser");
app.use(bodyParser.urlenconded({extended: true})

app.POST("/newfriends", (req, res)=>{
let newFriend = req.body.newFriend;
friends.push(newFriend=
	res.redirect("/friends")
})
```

API: application programming interface, interface por code to comunicate to one another.

Data format: XML y JSON(js object notation, like objetcs in js but everything is text)

Hacer request a un API.

Se usa el package "request"

```jsx
npm install request --save
const request = require("request")

request("url", (error, response, body)=>{
	if(!error && response.satatusCode == 200){
		console.log(body);
	};	
});
```

Siempre que se quiera acceder a la info de esa API,

hay que recordar que es un string, por lo que hay que transformarla en un objeto js, para eso

```jsx
request("url", (error, response, body)=>{
	const query = req.query.search; //search es el "name" que le damos al input
	const url = "url" + query;
	if(!error && response.satatusCode == 200){
		const parsedData = JSON.parse(body);
			res.render("results", {parsedData: parsedData})
	};	
});
```

Para los routes POST

```jsx
app.post("/eventos", (req, res) => {
  const name = req.body.name;
  const image = req.body.image;
  const newEvento = {
    name: name,
    image: image,
  };

  eventos.push(newEvento);
  res.redirect("eventos");
});

//y en el html
<input  type="text" name="name" id="name" placeholder="Conferencia 2020..">
//el name indica lo que subis
```

DATABASE

Coleccion de datos, con una interfaz que nos permite interactuar con esos datos.

Hay dos tipos de db:

-relacionales (SQL): tabular y planos.

Se usan tablas, columnas y rows, y entre tablas se relacionan con un id generalmente. No son flexibles

-no relacionales (NoSQL): no tables, y estan nested y embeded (por ejemplo: comentario puede tener dentro autor y texto. Con las relacionales las tables debian unirse para objetener info de esa manera). en JSON y son mas flexibles. ⇒ MongoDB

MongoDB:  es una base de datos, que se compone de Colecciones, las cuales contiene distintos documentos. El formato de datos que utiliza se llama BSON, similar a JSON pero tipado, es decir que cada dato tiene un tipo asociado.

Como usar MongoDB:

1. Instalarlo
2. Ejecutar mongod.exe. Nos indica el puerto de coneccion
3. Abrir un terminal y escribir mongo, que abre la terminar de mongo
4. escribir: use nombreDeLaNuevaDb, si existe, la abre, sino la crea.
5. show dbs: me muestras las dbs. En este caso, no muestra la nueva que se creo porque esta vacia
6. db.dogs.insert({name: "Rusty", breed: "cachogo"}) ⇒ cree la coleccion "dogs" y le INSERTE los campos name y breed con su data

    db.dogs.insertOne({name: "Rusty", breed: "cachogo"}) 

    db.dogs.insertMany([{name: "Rusty", breed: "cachogo"}, {name: "Juliana", breed: "cachugu"}]). InsertMany es un array de objetos. No es necesario que todos los campos sean iguales/completos en todos los objetos 

7. show collections ⇒ me muestra todas las colecciones de ls db en la que estoy
8. db.dogs.find() ⇒ si no le especifico nada, me muestra toda la data de esa coleccion + ObjectId que automaticamente le asigna mongo

    db.dogs.find({legs: {$lte: 2}) ⇒ $lte significa less than, con menos de dos patas. El $ es un operador mongo

    db.dogs.find({legs: {$lte: 2}, orejas: {$gte: 1}) ⇒ busca respetando dos criterios, se separan con una coma cada criterio. $gte great than

    db.dogs.find( $or: [{legs: {$lte: 2}}, {orejas: {$gte: 1}}]) ⇒ busca con menos de dos patas o con mas de una oreja, es un array de dos objetos

9. db.dogs.find({name: "Rusty"})
10. db.dogs.update({name: "Rusty"}, {$set: {name: "Juliana"}}) ⇒ el primer objeto, es lo que buscamos actualizar, el segundo objeto, por lo que lo actualizamos. Se incluye $set, para indicar que solo quiero actualizar el nombre. Si no lo incluyo, me actualiza el nombre pero me borra toda otra data que pudiera contener

    db.dogs.updateOne({name: "Rusty"}, {$set: {name: "Juliana"}}) 

    db.dogs.updateMany({name: "Rusty"}, {$set: {name: "Juliana"}}, el otro objeto que quiero modificar ) 

11. db.dogs.remove({name: "Rusty})

    db.dogs.deleteMany({name: "Rusty})

    db.dogs.deleteMany({}) ⇒ borra todos los documentos de la coleccion y no se puede volver atras

    MONGOOSE: es un tool que nos permite interactuar mas facilmente interactuar con mongoDB. Object data modelling library

    ```jsx
    npm install mongoose --save
    const mongoose = require("mongoose");
    //se necesita conectarlo con la db
    mongoose.connect("mongodb://localhost/nameOfDB");
    //si no esta creada la db, la crea.

    //Para agregar data a la db, se debe indicar como luce ese data
    const dogSchema = new mongoose.Schema({
     name: String,
    	age: Number,
    temperament: String
    }); // se define los patrones de la data

    //Tomamos luego la Schema y la insertamos en un modelo y la guardamos como Perro
    const Perro = mongoose.model("Perro", dogSchema);
    //Entonces ahora la puedo usar para todas las operaciones CRUD
    Perro.find()/.update()/.remove() => contiene todos los modelos y operaciones

    //Para agregar un nuevo perro a la coleccion
    const julian = new Perro({
    name: "Julian",
    age: 33,
    temperament: "enojoso"
    });

    //se guarda a en la db. PERO para asegurarnos
    //que se guardo, agregamos una callback para que nos informe si hay error
    julian.save((err, perro)=>{
    	if(err){
    console.log("Algo salio mal"}
    	else{
    console.log("se guardo un perro en la db")
    console.log(perro);}
    });

    //otra forma de crear y guardar en un solo paso
    Perro.create({
    name: "Julian",
    age: 33,
    temperament: "enojoso"
    }
    function((err, perro) =>{
    	if(err){
    console.log(err)}
    else{....
    }
    }) 

    //para buscar:
    Perro.find({}, function(err, perro)=>{
    	if(err)...
    })
    ```