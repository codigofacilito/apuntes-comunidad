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

### 8 - Funciones

- Función
  - Se encarga de contener una porción de código que se puede reutilizar.
  - Se utiliza la palabra reservada `def` para definir la función
  - Se debe utilizar el estilo de snake case si el nombre tiene más de una palabra.
  - Los parámetros van dentro de los paréntesis.
  - Retorna cualquier tipo de datos con la palabra reservada `return`, incluso más de un datos a la vez.
  - Puede tener tantos parámetros como se necesite.
  - Los parámetros pueden tener valores por defectos, pudiendo omitir su valor a la hora de llamar la función.
  - Hacemos uso del `*` en los parámetros cuando no sabemos la cantidad de parámetros que se vana utilizar, creando una tupla.
  - Por convención se utiliza `args` para usar el **\*\***, y `kwargs` para **\***.
  - El uso de doble asterisco nos ajunta los parámetros en un diccionario.
  - En caso de que la función no retorna ningún valor su valor será `None`.
  - Los `name space` pueden coexistir.
  - Para cambiar el valor de una variable global utilizamos la palabra reservada `global`.
  - Para documentar nuestras fusiones hacemos uso de las triples comillas dentro del cuero de la misma.
  - Para ver la documentación de nuestra función a través de su atributo `____doc____`

```python
def create_name(name):
    return f'Hola {name}, bienvenido al curso de python 3'
 
def rest(val1, val2):
    """Resta de dos valores"""
    return val1 - val2
 
def create_user(name, last_name, age=18):
    return {
        'nombre': name
        'apellido': last_name
        'edad': age
    }
 
 
 
```

- Función lambda
  - Se hace uso de la palabra reservada `lambda`.
  
```python
my_funtion = lambda grade=0 : grade * 1.8 + 32
result = my_funtion(32)
print(result)
 
sin_parámetros = lambda : True
 
con_valores = lambda val, val1=10, val2=10 : val + val1 + val2
 
con_asterisco = lambda *args : args[0]
 
con_doble_asterisco = lambda **kwargs : args[0]
 
con_asteriscos = lambda *args , **kwargs : kwargs.get('key', False)
```

- Función map
  - En Python, la función map nos permite aplicar una función sobre los items de un objeto iterable.

```python
lista = [1,2,3,4,5]
resultado = map(lambda numero: numero * numero , lista)
 
lista_resultado = list(resultado)
print(lista_resultado)
```

- Funciones anidadas
  - Puede contener otras funciones dentro de funciones.
  - Para modificar el valor del parámetro dentro del `name space` de la función tenemos que hacer uso de la palabra reservada `nonlocal`.

- Decoradores
  - Se trabaja como mínimo con 3 funciones.
  - La palabra reservada `pass` indica que no va a ocurrir nada.
  - Para usar el decorador hacemos uso del símbolo de `@`.
  - Para pasar parámetros dentro de nuestra función decoradora hacemos uso de `*args` y `**kwargs`.

```python
# a, b, c
# a(b) -> c
def decorador(funcion):
    def nueva_funcion(*args, **kwargs):
        print('Podemos agregar código antes')
        result = funcion(*args, **kwargs)
        print('Podemos agregar código después')
        return result
    return nueva_funcion
 
@decorador
def fucion_a_decorar():
    print('Este es una función a decorar')
 
@decorador
def suma(val1, val2):
    return val1 + val2
 
funcion_a_decorar()
 
print('\n')
 
result = suma(16, 8)
 
print(result)
```

- Generadores
  - Tipo especial de función para crear una secuencia de datos.
  - La secuencia no se almacena en memoria RAM.
  - Hacen uso de la palabra reservada `yield`.

```python
def tabla_multiplicar(numero, maximo=10):
    for posicion in range(1, maximo + 1):
        yield numero * posicion, numero, posicion
 
for resultado, numero, posicion in tabla_multiplicar(9)
    print(numero, '*', posicion, '=', resultado)
```

### 9 - Clases

- Clases
  - Son los moldes de los cuales vamos a crear nuestro objetos.
  - Se declaran usando la palabra reservada `class`, conteniendo atributos que serán las variables y métodos las acciones a realizar.
  - En el nombre se utiliza la nomenclatura CamelCase.

- Métodos
  - Todos los métodos que contengan las clases reciben el parámetro de `self`, no es una palabra reservada, es una convención.
  - Pueden retornar tantos valores como necesitemos y aceptar una N cantidad de atributos.
  
- Atributos
  - Pueden ser creados dentro como fuera de la clases.
  - Para mantener un código legible hacemos uso del método `__init__` para inicializar los atributos de nuestra clase.
  
  ```python
  class User:
      def __init__(self, username='', mail=''):
          self.username = username
          self.mail = mail
 
  codi = User('Codi', 'codigo@codigofacilito.com')
  ```

- Tipos de atributos
  - Variables de instancias son las que le pertenecen a la instancia de la clase, estas no se comparten con más ninguna instancia.
  - Variables de clases solo les pertenecen a las clases y si pueden ser usadas por las instancias. Estas pueden ser utilizadas sin haber creado una instancia previamente.

- Métodos estáticos
  - Podemos usarlo sin tener una instancia de la clase.
  - Se decora el método con la etiqueta `@staticmethod`

 ```python
 class Triangulo:
     
    @staticmethod
    def area(base, altura):
        return (base * altura) / 2
  ```

- Métodos de clase
  - Al igual que los métodos estáticos se pueden llamar sin la necesidad de instanciar la clase.
  - Se decora el método con la etiqueta `@classmethod`
  - Toman por convención en el primer parámetro `cls`
  
  ```python
  class Circule:
    pi = 3.14159265
 
    @classmethod
    def area(cls, radio):
        return cls.pi * radio ** 2
  ```
  
- Herencia.
  - Todas las clases se heredan de la clase `Object`.
  - A diferencia de otros lenguajes de programación, Python si soporta la herencia múltiple.
  - La clase padre se coloca dentro de los paréntesis de la clase hijo, siendo pisible utilizar todos los métodos de la clase padre.

  ```python
  class Animal:

      def comer(self):
          print('Comiend')

  class Perro(Animal):

      def __init__(self, nombre):
          self.nombre = nombre

      def ladrar(self):
          print(self.nombre, "esta ladrando")
  ```
  
- Sobreescritura de métodos
  - Solo debemos sobrescribir el nombre del método de la clase padre en nuestra clase hijo, y añadir las nuevas funcionalidades.
- Clase Object
  - Contiene métodos útiles.
  - Al utilizar el método `__str__` podemos obtener el valor que queramos visualizar en vez de la dirección en memoria del objeto.
  - La función `__dict__` nos devuelve todas las propiedades de nuestro objeto en forma de un diccionario.

### 9 - Módulos y Paquetes

- Módulos
  - Definen clases y funciones.
  - Para hacer uso de un módulo, utilizamos la palabra reservada `import` y el nombre del módulo que deseamos importar.
  
  ```python
  import caluladora
 
  result = calculadora.suma(11, 11)
    ```

  - La palabra reservada `from` no ayuda a importar de forma más fácil e intuitiva.
  - Al hacer uso del * importamos todos los métodos del modulo.
  
  ```python
  from caluladora import *
 
  result = suma(11, 11)
    ```

  - Para importar módulos más específicos solo sustituimos el * por el nombre de la función a utilizar. En caso de que se mas de una fución las separamos por coma.
  
  ```python
  from caluladora import suma, resta, division
 
  result1 = suma(11, 11)
  result2 = resta(11, 11)
  result3 = division(11, 11)
    ```

  - La palabra reservada `as` no da la posibilidad de renombrar nuestras importaciones.
  
  ```python
  from caluladora import suma as mi_suma
 
  result = mi_suma(11, 11)
    ```

  - Al crear módulos es buena práctica documentarlos al igual que las funciones y clases.
  - Para ver su documentación podemos hacer uso de la función `help()`.
  - La función `dir()` nos retorna una lista de todos los objetos que contiene nuestro módulo.
  - El archivo principal siempre tendrá por nombre `__main__`.

- Paquetes
  - Debe contener un archivo llamado `__init__.py` para que Python lo identifique como paquete.
  - El nombre del paquete estará dado por el nombre del la carpeta.
  - Para importar el paquete hacemos uso de `from`, el nombre del paquete, y especificamos de donde vamos a importar nuestras clases o funciones.
  - En el archivo `__init__` podemos exponer clases, funciones y objetos del módulo, sin la necesidad de especificar de dónde y qué tenemos que importar.

- Anotaciones
  - Fue incorporada a partir de Python 3.5
  - Se utiliza una flecha para indicar el valor que retorna nuestra función.
  - Si necesitamos colocar valores por defecto a nuestros parámetros en la función, los colocamos de derecha a izquierda despuespues del tipo de objeto.
  - Al usar anotaciones en nuestro código es más fácil de leer y comprender.

  ```python
  def saludo(nombre: str) -> None:
      print("Hello", nombre)
  
  def suma(num1 : int = 0, num2 : int = 0) -> int:
      return num1 + num2
 
  ```

- Comprehension
  - Nos permiten crear estructuras de datos más fácil.
  - Reduce la cantidad de línea de código.
  - Podemos usar todos los objetos iterables para su creación.

```python
result = [x for x in range(0, 100)]
 
dictionary = {index:value 
                for index, value in enumerate(result)}
```
