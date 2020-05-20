# C#

Created: May 07, 2020 8:20 PM
Reviewed: No

Lenguaje orientado a objetos.

Trabaja con librerias de la plataforma .NET, para programar aplicaciones de consola, escritorio, web y mobile.

IDE: Visual Studio

Comentarios:

```jsx
///<summary>
/// Comentario de una sola linea
///</summary>
/* Comentarios de varias lineas, para no poner el ///
*
* 
*/
```

Lo que esta entre <summary> son comentarios que luego podran exportarse a xml. Debe tener una etiqueta de entrada y salida.

```jsx
namespace Csharp{
	static class Program{
		static void Main(){
			}
		}
	}

///main = metodo principal del programa, por el cual indicamos como va a trabajar el programa en si

```

Variables: espacio de memoria reservado que almacena un dato.

Cada variable lleva un tipo:

-string: tipo de dato de texto

-int: tipo de dato integer, numero de dato entero, positivo o negativo.

-uint: dato entero positivo siempre

-float: decimal. 35.5f (poner la f)

-double: tambien decimal pero con mas presicion.

-decimal: numero decimal pero para numeros muy grandes

-byte: hasta el numero 255, para guardar medidas pequeñas. 

-bool: datos booleanos true/false

-DateTime fecha = DateTime.Today; ⇒se guarda la fecha de hoy

fecha.toShortDate.toString()

fecha.Year.

fecha.Month

Cuando tengo varias variables del mismo tipo:

int num1, num2, num3;

num1 = 12; num2 = 20; num3 = 15;

Cada sentencia debe finalizar con un ;

Convertir tipo de datos: num1.toString() ⇒ convierte la variable a texto

- Cuando trabajo con botones en un formulario:

```jsx
//luego de creado el boton Cerrar y doble click sobre el mismo
Application.Exit();

```

- Todo programa en c# debe estar adentro de una clase. No puede haber dos clases con el mismo nombre dentro de un mismo namespace. Si tienen un namespace diferente cada clase, puede haber dos clases con el mismo nombre dentro de un mismo programa.
- Existen clases propias y clases predefinidas(bibliotecas de clase/ API, como Console). Console se encuentra dentro del espacio de trabajo System, que se require al principio "using System"

```csharp
using System;

namespace Programa1{
	class Program{
		static void Main(string[] args){
			Console.WriteLine("Hello world);
			}
		}
	}

```

- Conversion explicita: almacenar un long en un int, primero hay que convertir el long a int (int)numeroLargo ⇒ esta conversion se llama casting
- Conversion implicita: almacenar un int en un long, no hay conversion, se hace implicitamente, porque no hay perdida de informacion

```csharp
Console.WriteLine("Ingrese un numero");
int rta1 = int.Parse(Console.ReadLine())
```

int.Parse() convierte un string en un int

- const ⇒ con variables cuyo valor no cambia. Deben inicializarse al momento de declararla. Y el nombre es buena practica ponerlo en Mayuscula

```csharp
const int num1 = 14;
```

- Metodos: grupo de sentencias/instrucciones a las que se da un nombre identificativo y que realizan una tarea en concreto en un momento determinado (cuando el metodo es llamado)

```csharp
TipoDevuelto nombreMetodo (parametros){
	cuerpoDelMetodo;
}

int sumaDeNumero (int a, int b){
  int rdo = a + b;
	return rdo;
}
```

Todos los metodos deben ir siempre dentro de una clase. 

Palabra metodo y palabra funcion es lo mismo (tanto si devuelve valor o no)

Un metodo void nunca llevara la palabra return, no devuelve nada ⇒ da error de compilacion.

-Metodo main: no devuelve datos, lleva un array de strings. Punto de entrada a la hora de ejecutar un programa, es estatico porque todavia no hay ningun objeto creado.

-static: metodo pertenece a la clase, y al llamarlo no se debe utilizar un objeto en la llamada.

```csharp
static void Main(string[] args){
	 mensajeEnPantalla();
}

static void mensajeEnPantalla(){
	Console.WriteLine("Mensaje en Pantalla");
}
 //para llamar al metodo, debe hacerse dentro del metodo Main, pero para eso
//el metodo o debe ser static o necesita un objeto para poder ser llamado, por
//eso se le agrega static
```

- Campos de clase: variables declaradas con ambito de clase (se declaran dentro de una clase y fuera de un metodo, puede ser accedida por cualquier metodo dentro de esa clase)
- Sobrecarga de metodos: cuando en la misma clase existen dos o mas metodos con el mismo nombre. Pero para ello, debe haber dos o mas metodos que tengan diferentes tipos de parametros o distinta cantidad de parametros
- Parametros por defecto: permite hacer "sobrecargas" y tener la misma cantidad y tipo de parametros y/o trabajar con otros programas que no aceptan sobrecargas:

```csharp
int sumaDeNum( int a, int b, int c = 0){
	return a + b + c;
}
// ! los parametros por default, deben ir luego de los parametros obligaotrios
	//requeridos
```

- Estructuras de flujo:
1. Condicional if: 

```csharp
if(condicion){
	codigo a ejecutar;
}

int age = 10;

if(age >10) Console.WriteLine("Eres un niño");
else Console.WriteLine("Eres un adulto");
```

- Generar numeros aleatorios

```csharp
Random numero = new Random();
int numAleatorio = numero.Next(0,100)
//crea un numero aleatorio entre 0 y 100
```

- Excepciones: errores cuando se ejecuta el programa que escaán al control del programador ( acceder a ficheros inexistentes, que la base de datos no conecte, etc). Para evitar que al producrise el error, el resto del programa no se ejecute, existe la "captura de excepciones/errores) ⇒ decirle al programa que hacer cuando se produzca el error (try, catch)

```csharp
try{
//codigo a ser suceptible de error
}
catch( tipoDeExcepcion err){
//codigo que indica como que hacer antes esa excepcion
}

//Ejemplo:

try{
	num = int.Parse(Console.ReadLine());
}
catch (FormatException err){
	Console.WriteLine("No has introducido un valor numerico. Tomaremos el 0 como valor");
	num = 0;
}
catch (OverflowException err){
	Console.WriteLine("Has introducido texto y se requeria numero. Tomaremos el 0 como valor");
	num = 0;
}

```

Herencia de excepciones:

Exception ⇒ SystemException ⇒ FormatException / OverflowException.

Si bien "Exception" cubre todas las excepciones, es de buena practica, utilizar la excepcion que corresponda (en caso que la envergadura del programa lo permita)

```csharp
try{
 /////
}
catch (Exception e) // se podria haber escrito tambien solo catch, pero no es buena practica
{
///
}
```

Siempre escribir primero desde la excepcion mas especifica hasta la mas general.

Sino, utilizar filtros:

```csharp
try{
///
}
catch (Exception e) when (e.GetType() != typeof(FormatException)){
///
}

//GetType(): objeto que pertenece a e, que te muestra el tipo de excepcion que agarra e =>
//"mientras la excepcion no sea del tipo FormatException, usar Excepcion general"
```

-Excepciones de tipo desbordamiento: exiten excepciones que C# deja pasar por alto y devuelve valores extraños, se trata del caso de excepciones por desbordamiento, es decir, cuando a una variable, por ej, del tipo int, termina almacenando un valor mas grande del que puede contener ese tipo. En este caso C# devuelve un numero negativo muy grande. Para evitar este comportamiento, se utiliza la expresion checked:

```csharp
checked{
	 int num = int.MaxValue;
		int rdo = num + 20;
	Console.WriteLine( rdo);
}
//ahora con checked, el programa no sigue corriendo y salta el error.

//tambien se puede hacer que este checked lo verifique automaticamente Visual Studio: 
//Proyecto => Propiedades => Compilacion => Avanzadas => Comprobar desbordamiento

```

Existen tambien la expresion unchecked ⇒ cuando quiero que c# se pase por alto una excepcion

! Solo funciona checked para int y long, no para double y float.

Otra forma de   manejar excepciones es con throw, que obliga a que existe un bloque try catch:

```csharp
public static string saludo(int num){
	switch (num){
	case 1:
		return "Hola";
	case 2:
		return "Adios";
	default:
		throw new ArgumentOutOfRangeException();
	}
}
//entonces en Main
try{
	Console.WriteLine(saludo(3);
}
catch(Exception e){
	Console.WriteLine($"Mensaje de la excepcion {e}");
}

//De esta forma, se captura la excepcion, salta el mensaje pero el programa
//sigue corriendo las lineas debajo
finally{

	Console.WriteLine("Esto se ejecuta salte o no la excepcion")
}
```

POO: Programacion Orientada a Objetos

Un objeto tiene un estado, propiedades y un comportamiento.

Los programas quedan divididos en partes, trozos, modulos o clases ⇒ Modularizacion. Esto permite que el programa sea reutilizable ⇒ Herencia.

Si existe algun fallo, el programa continua operando ⇒ handle excepctions.

Encapsulamiento.

1. Clase: modelo que contiene las caracteristicas comunes de un grupo de objeto. Una plantilla/modelo y tiene objetos que deriban de esa clase.
2. Objeto: Tienen propiedades(atributos) y comportamientos(que es capaz de hacer: metodos/funciones). Intancias: crear objetos que pertenezcan a una determinada clase

Como crear una clase: [//mo](//model)lde para crear objetos

```csharp
namespace EjemploPoo
{
	class Program{
			static void Main (string[] args){
				Circulo miCirculo; //creacion del objeto. Es una variable de tipo Objeto
				miCirculo = new Circulo(); //instanciacion de la clase. iniciacion de variable, se le dio un valor
				Console.WriteLine(miCirculo.calculoArea(2));

			}
		}
	class Circulo{
		const double pi = 3.1416; //definir una variable dentro de una clase es definir su propiedad/su campo de clase
		public double calculoArea(int radio){ //metodo de clase, que pueden hacer los objetos de tipo Circulo
			return pi * radio * radio;
		}	
	}
}
```

## Encapsulacion

Encapsulacion: proteger el codigo dentro de una clase de acceso externo. Los datos de una clase no sean accesibles por otra clase externa, a menos que uno lo requiera.

Esto se logra con las palabras public y private delante de la variable: si ponemos private, esa constante solo es accesible dentro de esa clase.

Los identificadores public deben comenzar con mayuscula. Los que no son public, comienzan con minuscula.

## Constructores

Estado inicial del objeto (caracteristicas y metodos iniciales). Es un metodo que tiene el mismo nombre que la clase, no devuelve datos y no es void.

```csharp
class Coche{
	public Coche (){ //metodo constructor
		ruedas = 4; //todos los objetos de clase Coche, tendran 4 ruedas
}

public int getRuedas(){ //metodo getter de acceso
		return ruedas; 
	}

	private int ruedas;
	private int puertas;
	private double largo;
	private double ancho;
	private String tapizeria;
	private bool climatizador;
}

class Program{
	static void Main (String[] args){
			Coche coche1 = new Coche(); // crea una instancia de la clase coche, instanciar la clase coche
//new => llama al constructor, da un estado inicial al coche
			Console.WriteLine(coche1.getRuedas());)
		}
	}
```

Para poder accedes a una propiedad de la clase Coche, no se puede acceder con punto, porque las propiedades se encuentran encapsuladas y no se puede acceder por fuera de la clase Coche (no es buena practica cambiarla a public). 

Para ello se debe crear un metodo de acceso (metodo Getter, nos dan informacion de propiedades).

Se puede dar sobrecarga de constructores: cuando no queremos que el estado inicial de todos las instancias de esa clase tengan los mismos atributos. No hay limite de constructores,  pero cada constructor tiene que tener distinta cantidad/tipo de argumentos, asi c# los puede destinguir.

Tambien puede pasar de no declarar un constructor. Si no lo declaramos, c# crea un "automaticamente" que estara vacio.

### metodo setter :

Establecen propiedades a los objetos. No devuelven informacion (como los getters).

```csharp
public void setExtras (bool climatizador, String tapiceria){
	this.climatizador = climatizador; 
	this.tapiceria = tapiceria;
}
//Diferenciar entre campo de clase y parametro

//en Main
coche3.setExtras(True, "Cuero");

public String getExtras(){
	return "Extras del coche: " + tapiceria + climatizador;
}
```

- Metodos que reciben de parametro un objeto

### Clase Math

```csharp
Math.Sqrt() => raiz cuadrada
Math.Pow() => 
```