# NodeJs Bootcamp

Created: May 08, 2020 8:16 PM
Reviewed: No

Node para trabajar asincronicamente, utiliza callbacks(err, data) -mas comun- y promises (E6 es async y await)

////////////////////////////SUMARIO DE PASOS////////////////////////////////

```jsx
npm init
npm install --save express ejs mongoose body-parser

//crear todas las variables de lo que instalamos
//llamar express

//Configurar la app
app.set("view engine", "ejs");
app.use("express.static("public");
app.use(bodyParser.urlencoded({extended: true});
mongoose.connect("mongodb//localhost/nombreDb");

//Configurar mongoose y el schema/model

const nombreSchema = new mongoose.Schema({
 //configuraciones
});

const nombreModel = mongoose.model("NombreModel", nombreSchema);

//Empezar con las routes

```

////////////////////////END SUMARIO DE PASOS////////////////////

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

## Express

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

Es comun que la primer pagina al abrirse un sitio, sea index, para eso:

```jsx
app.get("/", (req, res) => {
  res.redirect("/blogs");
});
```

# Database

Coleccion de datos, con una interfaz que nos permite interactuar con esos datos.

Hay dos tipos de db:

-relacionales (SQL): tabular y planos.

Se usan tablas, columnas y rows, y entre tablas se relacionan con un id generalmente. No son flexibles

-no relacionales (NoSQL): no tables, y estan nested y embeded (por ejemplo: comentario puede tener dentro autor y texto. Con las relacionales las tables debian unirse para objetener info de esa manera). en JSON y son mas flexibles. ⇒ MongoDB

## MongoDB

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
    Perro.find({}, (err, perro)=>{
    	if(err)...
    })
    ```

    ***********

    Cuando tengo un button/link, que hace referencia a otra route, por ejemplo, en href:

    ```jsx
    <a href="/eventos/<%= evento._id %>" class="btn btn-danger">Mas info</a>

    //SHOW - me muestra mas info de un perro en particular
    app.get("/perro/:id", (req, res) => {
      Evento.findById(req.params.id, (err, foundPerro) => {
        if (err) {
          console.log(err);
        } else {
          res.render("show", {perro: foundPerro});
        }
      });
    });
    ```

    ## Restful API

    REST: Transferencia de Estado Representacional, es un modelo de arquitectura web basado en el protocolo HTTP para mejorar las comunicaciones cliente/servidor. Una API es RESTful porque aplica la aquitectura REST.

    RESTFUL Routes:

    nombre    path         verb        purpose // Mongoose method                                                 

    ===============================================

    INDEX      /dogs        GET        lista de perros  // Dog.find()

    NEW        /dogs/new  GET      muestra formulario crear nuevo perro // n/a

    CREATE    /dogs         POST    crea un nuevo perro y add a db, redirige a                        

                                                    algun otro lado //    Dog.create()                    

    SHOW     /dogs/:id     GET      muestra info sobre un perro espec 

                                                    //Dog.findById()

    EDIT        /dogs/:id/edit  GET   Muestra formulario de edicion de un perro

                                             //Dog.findById()

    UPDATE   /dogs/:id     PUT       Actualiza a un perro espec, luego redirige

                                              //Dog.findByIdAndUpdate()

    DESTROY  /dogs/:id     DELETE Elimina un perro escp, luego redirige

                                               //Dog.findByIdAndDelete()

    *Navegacion entre carpetas(path) 

    `/` means go back to the root folder, then traverse forward/downward.

    `./` means begin in the folder we are currently in (current working directory) and traverse forward/downward in the tree.

    `../` means go up one directory, then begin the traverse.

    ```jsx
    //Referencia al route SHOW
    <a  href="/blogs/<% blog._id %>">

    //como hacer que encuentre la ruta para ese ID
    app.get("/blogs/:id", (req, res) => {
      Blog.findById(req.params.id, (err, foundBlog) => {
        if (err) {
          res.redirect("/blogs");
        } else {
          res.render("show", { blog: foundBlog });
        }
      });
    });
    // y luego crear SHOW template
    ```

    *Acortar las fechas:

    ```jsx
    blog.created.toDateString()
    ```

    *Acortar texto a mostrar:

    ```jsx
    <p><%- blog.body.substring(0, 100) %>...</p>
    ```

    ```jsx
    //Referencia al EDIT route
    //1. Editar el route
    app.get("/blogs/:id/edit", (req, res) => {
      Blog.findById(req.params.id, (err, foundBlog) => {
        if (err) {
          res.redirect("/blogs");
        } else {
          res.render("edit", { blog: foundBlog });
        }
      });
    });

    //en el template para que ya venga cargado lo que teniamos
    <div class="field">
                <label for="title">Titulo</label>
                <input id="title" type="text" name="blog[title]" value="<%= blog.title %>">
            </div>

    ```

    UPDATE route: Con respecto al metodo PUT, no existe (al igual que Delete) Iba a incluirse en HTML5, pero al parecer era muy dificil y no se incluyo.

    [https://softwareengineering.stackexchange.com/questions/114156/why-are-there-are-no-put-and-delete-methods-on-html-forms](https://softwareengineering.stackexchange.com/questions/114156/why-are-there-are-no-put-and-delete-methods-on-html-forms)

    Entonces, para estos dos casos:

    1. En el metodo del formulario de EDIT debe usarse POST
    2. En action:

        ```jsx
        action="/blogs/<%= blog._id %>?_method=PUT"
        ```

    3. 

    ```jsx
    npm install method-override —save
    const methodOverride = require("method-override")
    app.user(methodOverride("_method") //_method indica que si el request tiene _method se fige si es PUT o DELTE y lo trate asi
    ```

(Se podria crear otro route para hacer el update, pero no se seguiria la arquitectura REST)

  4.  

```jsx
app.put("/blogs/:id", (req, res) => {
  Blog.findByIdAndUpdate(id, newData, callback);
});

//Ejemplo:
app.put("/blogs/:id", (req, res) => {
  Blog.findByIdAndUpdate(req.params.id, req.body.blog, (err, updatedBlog) => {
    if (err) {
      res.redirect("/blogs");
    } else {
      res.redirect(`/blogs/${req.params.id}`);
    }
  });
});
```

SANITIZAR LAS ROUTES

```jsx
npm install --save express-sanitizer
const expressSanitizer = require("express-sanitizer")

app.use(expressSanitizer()); //siempre poner despues de body-parser
```

Esto se realiza en CREATE y UPDATE

```jsx
//Create
app.post("/blogs", (req, res) => {
    //sanitize
    **req.body.blog.body = req.sanitize(req.body.blog.body);**
  Blog.create(req.body.blog, (err, newBlog) => {
    if (err) {
      res.render("new");
    } else {
      res.redirect("/blogs");
    }
  });
});
```

Con esto, si al momento de ingresar un post, la persona quiere ingresar un script, no se renderiza ni se activa

## Asociaciones

Associations:  permite que multiples colleciones en el db se relacionen entre si (eventos, usuarios, comentarios)

-One:one: una entidad relacionada con otra entidad

-One:many: 

-many:many: libros y autores

1. Embedding data

Un usuario puede tener varios posts, pero un post un solo user.

```csharp
//POST
const postSchema = new mongoose.Schema({
	title: String,
	content: String
});
const Post = mongoose.model("Post", postSchema);

//USER
const userSchema = new mongoose.Schema({
	email: String,
	name: String,
	posts: [postSchema] //array of posts
});
const User = mongoose.model("User", userSchema);

const newUser = new User({
	email: "charlie@gmail.com",
	name: "Charlie"
});

newUser.posts.push({
	title: "nuevo post",
	content: "kljñdlskjfñsldf"
})
newUser.save((err, user)=>{
	if(err){
	console.log(err)}
else{
	console.log(user)}
})

const newPost = new Post({
	title: "nuevo post",
	content: "kjsñdljfañldfj"
});
newPost.save( (err, post)=>{
	if(err){
	console.log(err)}
else{
	console.log(user)}
});

//con embeded data, los posts fueron almacenados en un array (el post completo, con su titulo y su content

```

2. Reference Data - Object Reference

```csharp
//con objetct reference, los posts seran almacenados tambien en un array dentro de user
//pero se almacenaran a traves de un objeto

//USER
const userSchema = new mongoose.Schema({
	email: String,
	name: String,
	posts: [{ //array of objects id
		type: mongoose.Schema.Types.ObjectId,
		ref: "Post"
	}] 
});

//crea los posts y le asigna un ID al array en posts
const User = mongoose.model("User", userSchema);
Post.create({ //se crea el post independiente del user
	title: "hola2",
	content: "klajsklaj"
}, (err, post){
 User.findOne({email: "jose@gmail.com"}, (err, foundUser)=>{
	if(err){
		console.log(err)}
	else{
	foundUser.posts.push(post);
	foundUser.save((err, data)=>{
	if(err){
	console.log(err)}
	else{
	console.log(data}
			}
		}
	})
});

User.create({
	email: "jose@gmail.com",
	name: "Jose"
})

//traducir ese object en la data del post
User.findOne({email: "jose@gmail"}).populate("posts").exec((err, user)=>{
	if(err){
	console.log(err(}
	else{
	console.log(user)}
});
```

## Autenticacion

Vamos a utilizar PassportJs ⇒ para implementar autenticacion.

                           Passport-local ⇒ para username y password

                     Passport-local-mongoose ⇒ para trabajar con mongoose

Sessions: Http es un protocolo "sin estado" ⇒ cuando se envian request, los mismos no contienen informacion sobre nuestro historial, o request anteriores. A traves de las sesiones, podemos mantenernos logueados y seguir asi. Proveen un estado ("state") ⇒ encoded information.

Las sesiones nos dan estado en el protocolo y nos permiten estar logueados.

Se instalan los paquetes express, mongoose, passport, body-parser, passport-local, passport-local-mongoose y express-session, ejs

```csharp
//Pasar usar las features de mongoose-passport
//En User Model

const mongoose = require("mongoose");
const passportLocalMongoose = require("passport-local-mongoose");

const UserSchema = new mongoose.Schema({
  username: String,
  password: String,
});

// Load User authentication features. Agrega automaticamente la codificacion y decodificacion de las sesiones
UserSchema.plugin(passportLocalMongoose);

module.exports = mongoose.model("User", UserSchema);
```

Para usar passport en nuestra aplicacion

```csharp
const express = require("express");
const mongoose = require("mongoose");
const passport = require("passport");
const LocalStrategy = require("passport-local");
const passportLocalMongoose = require("passport-local-mongoose");
const bodyParser = require("body-parser");
const User = require("./model/user");

mongoose.connect("mongodb://localhost/secret_password");

const app = express();
app.set("view engine", "ejs");
// Se crea un secret message
app.use(
  require("express-session")({
    secret: "Love programming", //codificacion
    saveUninitialized: false,
  })
);
//Body parser lee y permite utilizar la data enviada en un formulario POST
app.user(bodyParser.urlencoded({extended: True})
//Inicializa passport
app.use(passport.initialize());
//Corre passport
app.use(passport.session());

//Metodos importantes: leen la sesion que se encuentra codificada(o si esta decodificada, la codifica)
passport.serializeUser(User.serializeUser());
//Toman la data de la session y la decodifican
passport.deserializeUser(User.deserializeUser());
```

Agregar signup/register formulario

```csharp
//Mostar formulario de registro
app.get("/register", (req, res) => {
  res.render("register");
});

//Manjear la data que el user envia (user y pw)
app.post("/register", (req, res) => {
  req.body.username;
  req.body.password;
//Se crea un usuario pero aun no esta guardado en la db.
//Y la clave no se agrega en el objeto, ya que no es buena idea guardala en la db
//User register  tomara esa password y la convertira en una larga cadena de string
//Y devolvera un usuario con nombre y clave encodeada
User.register(
    new User({ username: req.body.username }),
    req.body.password,
    (req, user) => {
        if(err){
            console.log(err)
            return res.render("register")
        }
//SI no hay error, va a correr passport authenticate y se encarga de loguear al user
//corriendo el seralized user definido
        passport.authenticate("local")(req, res, () => {
        res.redirect("/secret");
      });
    }
  );
});
```

```csharp
//Formulario en register
<h1>Sign up Form</h1>
<form action="/register" method="POST">
    <input type="text" placeholder="username" name="username">
    <input type="password" name="password" id="" placeholder="password">
    <button>Submit</button>
</form>
```

Con esto, cuando el usuario se registra, en nuestra db se creara el usuario con su nombre, su "salt" y su "hash", y no se guarda la clave en raw

Ahora, la logica del login

```csharp
//formulario
<h1>Login</h1>
<form action="/login" method="POST">
    <input type="text" placeholder="username" name="username">
    <input type="password" name="password" id="" placeholder="password">
    <button>Login</button>
</form>
```

```csharp
//Login routes
//
passport.use(new LocalStrategy(User.authenticate()));
//render login form
app.get("/login", (req, res) => {
  res.render("login");
});

//post login data
//Se usa el passport.authenticate dentro del app.post y no el callback
//Se trata de un middleware
app.post(
  "/login",
  passport.authenticate("local", {
    successRedirect: "/secret",
    failureRedirect: "/login",
  }),
  (req, res) => {}
);

app.listen(3000, () => {
  console.log("Server is running");
});
```

Middleware: codigo que corre antes del callback req, res  

Logout

```csharp
//No se necesita routes, solo un link
<li><a href="/logout">Logout!</a></li>

//EN app.js
//Cuando uno se desloguea, no hay transacciones con la db
//Passport destruye toda la data de la sesion
app.get("/logout", (req, res) => {
  req.logout();
	res.redirect("/");
});
```

Para evitar que el usuario pueda llegar a una ruta que solo se puede tener acceso una vez logueado, se debe crear un middleware que chequee si se esta logueado o no

```csharp
//Para eso creamos una funcion para chequear el if
function isLoggedIn(req, res, next) {
//req es el request object, res la response object y next es cosa siguiente a ser llamada
  if (req.isAuthenticated()) {
    return next();
//next se refiere a:
// res.render("secret"); (ver prox paso)
  }
  res.redirect("/login");
}
```

Esta funcion la debemos agregar en la ruoute que queremos proteger y que solo se acceda por los usuarios logueados

```csharp
app.get("/secret", isLoggedIn, (req, res) => {
  res.render("secret");
});
```