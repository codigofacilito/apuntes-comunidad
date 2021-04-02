# Notas del Curso profesional de Python

## Índice

### 2 - Conceptos Básicos

- Declaración de variables

  - Son direcciones en memoria y estas pueden cambiar el **valor** que almacenan.
  - Pueden contener valores **booleanos**, **cadenas de caracteres**, **número enteros** y **número con coma flotantes**.
  - El nombre de las variables deben ser descriptivos.
  - Se recomienda utilizar la sintaxis de **snake_case**, (separar las palabras con guiones bajos) y todas las palabras en minúsculas.
  - Las constantes en Python no existen, para esto se utiliza la nomenclatura de poner el nombre de la variable totalmente en mayúscula.
  - Como en todos los lenguajes **Python** también tiene su palabras reservadas, se pueden ver en este [aquí](https://www.programiz.com/python-programming/keyword-list).

  ```python
      pataform_name = "Código Facilito"
      year = 2021
      my_money = 15.5
  ```

- Asignación múltiple

  - Podemos asignar el valor a múltiples variables en un solo renglón.

    ```python
        name, year, my_money = "Cod", 2021, 15.5
    ```

- Operadores relacionales y lógicos

  - Relacionales:
    - `==`, `!=`, `<`, `>`, `>=`, `<=`
    - Se utilizan para comparar y su resultado es booleano.

  - Lógicos
    - `or` : **O** en español. Solo se necesita al menos uno de sus valores sea verdadero para obtener un resultado verdadero
    - `and` : **Y** en español. Deben ser todas las comparaciones verdaderas para obtener un resultado verdadero.
    - `not` : **NO** en español. Niega y obtiene valor contrario a la salida.

- Entrada de datos por teclado

  - Para obtener los datos en consola dados por el usuario se utiliza la función `input()`. Esta puede tomar un `String` como parámetro, el cual muestra en consola al usuario.

  ```python
  name = input('Entre su nombre: ')
  print(name)
  ```

- Comentarios

  - Para comentar  una sola línea de codigo se utiliza el símbolo `#`.
  - Cuando necesitamos más de una línea o documentar nuestro código utilizamos triple comillas `""" Comentario multilínea"""`.

---

### 3 - Listas

- Qué son las listas
  - Son una estructura de datos.
  - Estas son dinámicas, siendo posible que crecen o decrecen según nuestras necesidades.
  - Podemos almacenar x cantidad tipos de datos, inclusive otras listas.
  - Se pueden modificar los elementos que tengan almacenados.
  - Su longitud esta determinada por la cantidad de elementos que contenga.
  
- Índices y Sublistas
  - Cada elemento tendrá un índice único, empezando desde `0` y terminado en `longitud - 1`.
  - Podemos acceder con los índices negativos, tomando los valores de a tras hacia delante.
  
- Sub listas
  - Para crear una sublista se utiliza [desde:hasta]
  - Podemos obtener sublista con salto [desde:hasta:salto]
  
- Operadores comunes
  - El método `.append()` lo utilizamos para agregar un elemento nuevo a la lista.
  - Para ordenar los elementos que contengan utilizamos algún algoritmo en específico o el método `.sort()`.
  - Para obtener el valor maximo de la lista utilizamos la función `max()` y para el valor mínimo `min()`.
  - Para saber la longitud de nuestra lista hacemos uso de la función `len()`.
  - Para saber si existe determinado valor dentro de la lista nos apoyamos del la palabra reservada `in`.
  - Obtener el índice de un elemento con el método `.index()`.
  - El método `.count()` cuenta el elemento que se repite, en caso de no contenerlo devuelve 0.

  ```python
  # una longitud de 4 elementos
  my_mix_list = [2, "Hola", [3, 4, 5], 65.65]
  numbers = [5, 59, 12.05, 57, 32.58]
  cureses = ["Java", "Dart", "Python", 'PHP', "Java Script", "C++"]
 
  # sublista
  sub_list = curses[2:3]  # [[3, 4, 5],"PHP"]
 
  # ordenar lista
  numbers.sort()  # [5, 12.05, 32.58, 57]
 
  # operadores comunes
  minimo = min(numbers)  # 5
  maximo = max(numbers)  # 57
  len(numbers)  # 5
  result = 30 in numbers  # False
 
  ```

### 4 - Tuplas

```python
tupla = ('Estoy', 'estudiando', 'en', 'Código', 'Facilito')
```

- Tuplas
  - Al igual que las listas permiten almacenar diferentes tipos de datos, con la diferencias que son inmutables, no vamos a poder cambiar su contenido.
  - Esta se declara con los calores dentro de paréntesis, y sus valores estarán separados por comas.
  - No es posible hacer uso de los métodos que existen en las listas.

- Valores por índices
  - Los elementos se obtienen igual que en la lista, por el índice.

- Comprimir y Descomprimir tuplas
  - Es posible descomprimir la tupla si esta contiene la misma cantidad de variable a las cuales le vamos asignar.

- Desempaquetado de tuplas
  - Cuando no tenemos la misma cantidad de variables para descomprimir la tupla podemos usar el asterisco delante de determinada variable, para que Python se encargue de gestionar la asignación por nosotro de todos los valores que no tienen variable.
  
- De listas a tuplas
  - Cuando necesite convertir una tupla a list utilizamos la función `list()` y si lo necesitamos en sentido contrario de tuple a lista utilizamos la función `tuple()`
  - Los valores de la tupla no se modifican al convertirla a lista.

```python
tupla = ('Estoy', 'estudiando', 'en', 'Código', 'Facilito')
 
# Valor por índice
tupla[-1]  # 'Facilito'
tupla[:2]  # ('Estoy', 'estudiando')
 
# Desempaquetado de tuplas
val_1, val_2, val_3, val_4, val_5 = tupla
 
# De listas a tuplas
new_list = list(tupla)  # ['Estoy', 'estudiando', 'en', 'Código', 'Facilito']
my_list = [3, 34, 56, 0.34, 45.6]
new_tuple = tuple(my_list)  # (3, 34, 56, 0.34, 45.6)
 
```

### 5 - Cadenas

-No son más que cadenas de caracteres que tiene un orden establecido.

- Las cadenas son inmutables, no podemos cambiar su contenido.
  - Podemos tratarla de igual forma que las listas y tuplas para acceder a cada uno de los caracteres mediante su índice.
  - Los espacios son contados como caracteres.
  - Las cadenas pueden declararse con comillas simples o dobles, para usar las comillas simples dentro de una cadena, esta tiene que ser declara con comillas dobles
  - Para saber su tamaño nos apoyamos de la función `len()`.
  - El método `split()` nos ayuda a crear crear una lista a partir de la cadena que utilizamos. El separador por default es el **espacio**.
  - El método `join()` crea una cadena a partir de una lista.
  
- Formato y manipulación para cadenas
  - El método `.capitalize()` genera un nuevo String con la primera letra en mayúscula.
  - El método `.lower()` convierte todo los caracteres a minúscula y el `.upper()` para para convertir toda la cadena a mayúsculas.
  - Para dar formato podemos hacer uso de varios métodos:
  
  ```python
  val_1 = 'Python'
  val_2 = 'Uriel'
 
  result = "Curso de %s impartido por %s" %(val_1, val_2)  # Curso de Python impartido por Uriel
 
  result = "Curso de {} impartido por {}".format(val_1, val_2)  # Curso de Python impartido por Uriel
 
  result = f"Curso de {val_1} impartido por {val_2}" # Curso de Python impartido por Uriel
 
  ```

- Concatenación
  - Usamos el símbolo de `+`
  
- Búsqueda de cadenas
  - Hacemos uso del método `count()` y nos devuelve el número de veces que se encuentra el parámetro que estamos buscando
  - La palabra reservada `in` nos devuelve un valor booleano.
  - El método `find()` nos retorna la referencia donde se encuentra nuestro valor a buscar, en caso de no encontrar retorna -1.

```python
curse = "Curso profesional de Python"
examp = "I'm a person"
curse[-1]  # n 
len(curse)  # 27 caracteres de longitud
curse.split()  # ['Curso', 'profesional', 'de', 'Python']
 
# Concatenación
curse + 'en Código Facilito'  # Curso profesional de Python en Código Facilito
```

### 6 - Diccionarios

- Qué son los diccionarios
  - Almacenan diferentes tipos de datos.
  - Son mutables, siendo posible modificar todos sus valores.
  - Cada **valor** necesita una **llave** y viceversa.
  - Estos se declaran entre `{}` .
  - Para obtener un **valor** del diccionario solo necesitamos la llave.
- Obtener elementos de un diccionario
  - Para buscar determinada **llave** utilizamos `in`.
  - Pare evitar error si no existe el **valor** utilizamos el método `.get()`, este devuelve un **valor** definido por el dev si no encuentra nada.

- Llaves, ítems y valores
  - El método `.keys()` devuelve todas las key que contenga nuestro diccionario.
  - El método `.values()` devuelve todas las valores que contenga nuestro diccionario.
  - El método `.items()` devuelve en forma de tuplas con las key y el valor que contenga nuestro diccionario.
  
- Eliminar elementos
  - Nos apoyamos de la palabra reservada `del` para eliminar cualquier valor que contenga nuestro diccionario.
  - El método `.pop()` elimina el valor a partir de la llave dada.
  - Para eliminar todo el diccionario podemos hacer uso del método `.clear()` o asignar `{}` vacías.

```python
val_1 = {
  "nombre" : "Codi"
  "edad" : 5
}
 
val_1["edad"]  # 5
val_1["edad"] = 7
val_1["edad"]  # 7
 
result = "nombre" in val_1  # True
 
result = val_1.get('pais', 'error')  # Empty
 
```

### 7 - Ciclos y Condicionales

- Existen 4 Objetos iterables `listas`, `tuplas`, `string`, `diccionarios`
- Valores booleanos y valor None
  - Los valores booleanos solo pueden tener dos opciones, `True` o `False` (Verdadero o Falso en español).
  - Python también reconoce a los valores de `False`, `None`, `0`, `0.0`, `''`, `[]`, `{}` como **falsos**
  - En Python la palabra reservada `None` cumple la función de valor vacío.

```python
val = None
val_2 = False 
```

- Condicionales
  - Los condicionales nos permiten ejecutar porciones de códigos en dependencia de determinada condición que se cumpla o no.
  - Se usa la identación de 4 espacio por convención.
  - Hacemos uso de las palabras reservadas `if` `else` `elif`.
  - Todas las condiciones se evalúan de arriba hacia abajo, siempre empezando por `if`.

```python
semaf = 'verde'
 
if semaf == 'verde':
    print('Puedes continuar')
elif semaf == 'amarillo':
    print('Deténgase por un momento')
else:   
    print('No puede continuar')
```

- Ciclo while:
  - Podemos ejecutar tantas veces se requiera un bloque de código.
  - `while` es una palabra reservada.
  - Podemos hacer uso de la palabra reservada `else` para ejecutar código cuando la condición ya no se cumpla o se termina el ciclo.

```python
number = 202012851
count = 0
 
while number >= 1:
  count += 1
  number = number / 10
 
print(count)
 
```

- Ciclo for:
  - Recore todos los elementos de un objeto iterables.

```python
name = 'Código Facilito'
 
for i in name:
  print(i)
```

- Función Range y enumerate:
  - `renge()` crea una sentencia de numero que podemos iterar con el `for`. La secuencia siempre va a empezar por el número 0.
  - Podemos especificar donde comenzar y donde terminar `range(start, end)` y no se tomará en cuenta el número donde termina.
  - La secuencia puede empezar desde números negativos.
  - La función `enumerate()` nos da la posibilidad de hacer uso de dos valores, el índice y el valor del objeto iterable.
  - Se puede especificar a partir de donde va a empezar el índice de objeto iterable.
  - La palabra reservada `break` rompe el ciclo y `continue` rechaza todas las declaraciones restantes en la iteración actual del ciclo y mueve el control de regreso a la parte superior del ciclo
  
```python
name = 'Código Facilito'
 
for i in range(len(name)):
  print('Index:', i, 'Value:', name[i])
 
for index, value in enumerate(name):
  print('Index:', index, 'Value:', value)
 
```
