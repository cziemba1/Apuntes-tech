# Python

Created: May 14, 2020 8:04 PM
Reviewed: No

Python tiene dynamic typing: las variables pueden cambiar de tipo durante el programa

### Data Types

- Interpolation:

```python
name = f"hello this {name}"
```

- Conversion tipo de datos: int(), str(), float()

/// input() ⇒ pide info al usuario - siempre devuelve string, por lo que tendria que convertirlo a int/float en caso que sea numero///

-Numeros randoms: 

```python
import random
number = random.randint(0,2)
```

-string.lower() / string.uppercase()

## Looping

## for loop

Se loopea sobre strings, listas, rangos(iterable objects)

```python
for item in iterable_object:
	#do something
```

item hace referencia a la posicion actual del iterador dentro del objeto iterable. Recorrera dentro de cada item y luego desaparece

### Ranges

Secuencia inmutable de numeros y es comumente utilizado para loopear un numero especifico de veces en una sentencia for

```python
range(1,8,2) #empieza en 1, termina en 7 y va de dos en dos(step)

```

## While loop

Sirven tambien para iterar, pero lo hara mientras la condicion es verdadera, en el momento que se haga falta, se detiene

```python
while isTrue:
	#do Something

#Ejemplo
user_response = None #se debe declarar una variable de comienzo
while(user_response != "por favor"):
	user_response = input("Ah ah no dijiste la palabra magica")
#Ejemplo 2

num = 10
while ( num < 20):
	print(num)
	num += 1
```

## Lists

Coleccion de items agrupados, combinar data en un data structure. (arrays en js por ej)

```python
tareas = [1, 2, "hola", "comer", hola_mundo]
len(tareas) # devuelve la cantidad de items en la lista
"pintar" in tareas # Falso
"comer" in tareas # True

r = range(1, 10)
r2 = list(r)
print(r2)
# convierte r en una lista

```

### List methods

- Agregar simple data a lista

```python
data.append("purple") # => agrega al final de la lista
```

Para agregar una lista, al final de otra lista se usa extend

```python
list1 = [1,2,3,4]
list_completa = list1.extend([5,6,7,8])
print(list_completa)
# [1,2,3,4,5,6,7,8]
# si uso append quedaria asi
# [1,2,3,4, [5,6,7,8]]
```

Insert inserta un item en una posicion dada

```python
list = [1,2,3,4]
new_list = list.insert(2, 8)
print(new_list)
# 1,2,8,3,4 => inserta en la posicion 2 el numero 8

```

- remover items de una lista

-clear (remueve items de una lista)

```python
list.clear() # vacia toda la lista, no la elimina sino esta vacia
```

-pop: remueve un item en una posicion dada y lo devuelve, si no se especifica el index, remueve y devuelve el ultimo item de la lista

```python
list = [1,2,3,4]
list.pop(2)
# 3 => por si queres capturarlo y hacer algo con ese numero
```

-remove: remueve el primer valor que es x y no lo devuelve. Si no encuentra, tira error

```python
list = [1,2,3,4]
list.remove(2)
list = [1,3,4]
```

- index ⇒ si no encuentra, no tira error

```python
list = [1,2,3,4,5,6,6,7,7,7,7,7]
list.index(2) # 1 => me indica el index de 2
list.index(7, 8) # 8 => me devuelve el index de 7, a partir de la posicion 8
list.index(7, 5, 9) # 7 => me devuelve el index de 7 entre la posicion 5 y 9
# Siempre es el primero que aparece
```

- count ⇒ si no encuentra no tira error

Cuenta la cantidad de veces que aparece un tiem en la lista

```python
list = [1,2,3,3,3,3,4,5,5,6]
list.count(3) # 4
list.count(21) # 0

```

- revere ⇒ reversa los elementos de la lista, en la misma lista, no crea una nueva

```python
list = [1,2,3,4]
list.reverse()
print(list) # [4,3,2,1]
```

- sort ⇒ ordena los items en la misma lista, no crea una nueva
- join ⇒ es un string method, pero es comun convertir listas en string. Devuelve una nueva lista

```python
list = ["Hola", "Mr", "John"]
" ".join(list) # "Hola Mr John
".".join(list) # "Hola.Mr.John"
```

- slice ⇒ dame la parte de la lista desde hasta este. Genera una nueva lista utilizando los elementos de la sliced. Son Inclusive (inicio counting) y Exclusive (final couting)

```python
some_list[start:end:step] # => como range
list = [1,2,3,4,5]
list[1:] # [2,3,4,5] => incluye el que comienza
# Si se pasa un negativo, te corta esa cantidad desde el final
list[-4:] = [2,3,4,5] # => nueva copia, con su propio espacio en la memoria
list[:3] = [1,2,3] #=> No incluye el ultimo
list[1:4:2] = [2, 4]

list_2 = [1,2,3,4,5,6]
list_2[1::2] # [2,3,6]
list_2[::2] # [1,3,5]
list_2[1::-1] # [2, 1] => el step negativo me hace cambiar de direccion

# Se utiliza para reverse a string
string[::-1]
# Modificar porciones de una lista

numbers = [1,2,3,4,5]
numbers[1:3] = ["a", "b", "c"]
print(numbers) # [1, "a", "b", "c", 4, 5]
```

- swapping values ⇒ se utiliza para shuffling, sorting, algorithm

```python
names = ["Julian", "Pedro"]
names[0], names[1] = names[1], names[0]
print(names)
# ["Pedro", "Julian"]
```

### list comprehensions

```python
list = [1,2,3]
[item*2 for item in list] # devuelve una nueva lista
#[2,4,6]

[item*2 for item in list if item>2]
```

### nested list

```python
nest_list = [[1,2,3], [4,5,6], [7,8,9]]

for i in nest_list:
	for item in i:
		print(item)

```

## Dictionary

Estructura de datos que consiste en una palabra key(etiqueta) y su valor(data): key-value pairs

```python
#Crear dicccionarios:
#1.
instructor ={
	"sexo" = "mujer",
	"edad" = 28
}
#2.
instructor2 = dict(sexo="mujer", edad= 28)
#3. Cuando ya tengo una lista hecha de la cual quiero crear un dict
person = [["name", "Claudia"], ["edad", 19]]
dict = dict(person)

# Accesing data
instructor["sexo"] # "mujer"

#Iteration
#1. iterar sobre values
for value in instructor.values():
	print(value) # "mujer" 28
#2. iterar sobre keys
for key in instructor.keys():
	print(key)
#3. iterar sobre values y keys
instructor.items() # devuelve una lista de tuples
# dict_items[("sexo", "femenino"), ("edad", 28)]
#Utilizando el for
for key,value in instructor.items():
	print(key,value)
#sexo "mujer"
#edad 28

#Tiene un diccionario esta key?
"edad" in instructor # True
#Tiene un diccionario este value?
28 in instructor.values() # True
```

### Metodos en diccionarios

```python
#vaciar el diccionario, devuelve {}
instructor.clear() 

#hacer una copia de un diccionario existente
instructor2 = instructor.copy() 

#crear key-value pairs a partir de valores separados por coma, sobre iterables(se puede pasar strings o ranges)
new_user = {}.fromkeys(["name", "age"], "unknown")
print(new_user)
#{"name": "unknown", "edad": "unknown"}

#Testear si un valor existe en el dict sin que tire error si no esta, devuelve None
instructor.get("nombre") #None
instructor.get("edad") #28

#remover un key-value pair
instructor.pop("edad") #=> se le debe proveer la key
#28 // devuelve el valor que fue removido

#remover un key-value random
instructor.popitem()

#Agregar/actualizar valores
nombre = {"name": "Claudia"}
instructor.update(name)
```

### dict comprehensions

```python
dict = {"first": 1, "second": 2, "third": 3}

{key: value*2 for key,value in dict.items()}
#{"first": 1, "second": 4, "third": 6}

#Hacer un diccionario
{num: num*2 for num in [1,2,3,4]}

num_list = [1,2,3,4]
{num: ("even" if num%2 == 0 else "odd") for num in num_list}

#Juntar dos listas y hacer un dict
list1 = ["CA", "NG", "RI"]
list2 = ["CALIFORNIA", "NUEVA GUINEA", "RICA COSTA"]
answer= {list1[i]: list2[2] for i in range(0,3)}
```

## Tuples

Una coleccion ordenarada de items, es inmutable

```python
numbers = (1,2,3)
```

Son mas rapidas que las listas, mas seguras (porque no cambian) y pueden ser usadas como key en un diccionario (una lista no se puede usar como key)

```python
#se crean con () o tuple()
#se accede a la data con []

#para iteration se usa tambien for in
#Count => devuelve la cantidad de veces que esta una data en la tuple
tuple = (1,2,3,4, 2)
tuple.count(2) #2
tuple.index(3) #2
```

## Sets

Grupo de elementos no ordenados ⇒ no se pueden acceder mediante index, que no tienen valores duplicados (son unicos) .

```python
a = {1,2,3}
a = set(1,2,3)
3 in a # True

#se accede 
for i in a:
	print(i)

#agregar data => si ya esta la data no tira error
a.add(6)
#eliminar data => tira error si el item no esta
a.remove(3) 
#Eliminar sin que tire error cuando no este
a.discard(9)
#copia un set creando un nuevo set
b = a.copy()
#vaciar un set
a.clear()

```

# Functions

Proceso para ejecutar tareas