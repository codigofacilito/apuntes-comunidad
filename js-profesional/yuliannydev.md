# Curso Profesional de JavaScript
## Apuntes de @yuliannydev

- Autor/Fuente: Uriel Hernandez
- Categoría: JavaScript
- Estatus: Estudiando
- Periodo: Mar 29, 2021 → Apr 1, 2021
- Resumen: Yes


**Índice del Curso:**

---

## **INFORMACIÓN RELEVANTE:**

---

- ✅ **Ideas más importantes del Curso:**
    1.  
    2.  
    3. 
- 📕 **El Curso en un párrafo o idea:**
    - 
- **🔗 Ligas, documentos y medios importantes:**
    - 

## **RESUMEN DEL CURSO:**

---

## Parte 1: Introducción

- alert("Mensaje de alerta en el navegador");
- prompt(); // Sale la ventana emergente en el navegador pidiendo un dato. La funcion prompt da como resultado lo que se haya escrito adentro de la ventana.

## Parte 2: Conceptos Básicos

- Cómo es Js técnicamente.
    - Js se compila en tiempo de Ejecución.
    - Es un lenguaje interpretado, y el interprete es el navegador.
    - Al ser un lenguaje que compila en ejecución, los errores se consiguen en el momento que se esté leyendo dicha línea.
    - Js es un lenguaje débilmente y dinámicamente tipado. (Dinamico porque la misma variable puede ser utilizada para un int, o string. Y debil porque no se evalua el tipo de dato hasta que el programa se compila)

        Si al compilar no se corrigen los tipos, es que es un lenguaje débilmente tipado.

    - Es case sensitive: Distingue MAYUS de minúsculas.
- Variables y constantes.
    - Una **var**iable es una acción en memoria a la cual se accede a ella mediante un identificador.
    - La naturaleza de una variable radica en su nombre, es decir, mientras que el programa está en ejecución se le puede reaccionar un valor a ese espacio de la memoria.
    - Las constantes tienen un valor fijo. Una vez que se le da un valor en memoria, este no puede ser modificado.
    - Las constantes sirven para optimizar el código.
    - Cuando se usa **const** el programa sabe exactamente cuando espacio en memoria necesita.
    - Las variables son dinámicas y requieren cálculos mientras el programa se está ejecutando para reasignar espacio en la memoria.
- Números y Operaciones aritméticas.
    - Los operadores **mat** se usan al igual que en las matematicas (+, -, *. /) Excepto % que se usa para obtener el residuo de una división, ej:

    **10 % 2 = 0**
    Donde cero es el residuo de la división de 10 / 5.

    - En js existe una libreria **mat.**

    NOTA: Una librería es el código que ha realizado alguien más y nosotros podemos utilizar.

    **Math.PI** //3.1416

    - Métodos que se pueden usar por Math:

    [Math](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math)

- Booleanos.
    - Sirven para dar un Sí, o un No, con **true** y **false.**
    - Sirve para notificaciones.
    - Los valores reales en Js se evalúan como verdaderos al obtener su valor booleano.

    ```jsx
    Cómo obtener el valor booleano de un número

    let booleano = new Boolean(1);
    console.log(booleano.toString());

    Los num reales en Js tiene como valor **true.**
    ```

    - Los valores que dan false son:

    undefined, NaN, null, 0, -0, "", false.

- Operadores de comparación.
    - Comparación **==**
    - Desigualdad ! =
    - Mayor que >
    - Menos que <
    - Mayor igual que > =
    - Menos igual que < =
    - En JS el operador == ignora los tipos de datos que se están comparando, es decir:

    ```jsx
    24 == "24";
    //true

    Porque a pesar de que uno es un num y el otro un string, conservan el mismo valor.
    ```

    - Para hacer comparaciones estrictas, mismo dato y tipo de dato se usa ===.
    - Para que sean diferentes en valor y en tipos ! ==
    - Los oepradores de comparación se acompañan de los operadores lógicos.
- Operadores lógicos.
    - Estos se acompañan de los booleanos y nos permiten saber si en conjunto son verdaderas o falsas.
    - &&, ||, !.
    - && retorna true si ambas expresiones son iguales.
    - || solo una expresion tiene que ser true. Una vez que encuentra un true, ya no evalúa mas esa expresión, porque es irrelevante.
    - ! tiene como funcion negar, es decir **!false** es true.
- Condiciones.
    - Bloque de código que se ejecuta si su criterio se cumple.
    - Cuando evalúa un bloque con multiples elseif, solo evalúa uno como verdadero. Es decir, si varias de las condiciones se cumplen, solo ejecutara la primera.
    - else solo se ejecuta si ninguna de las anteriores se cumple.
- Ciclos.
    - Los ciclos nos ayudan a ejecutar un bloque de código varias veces.

    Nota: Programas a veces se trata de encontrar patrones, es decir, hallar una relación entre números para tener una formula, o a veces un mismo paso que se repite y cambia ligeramente.

    - Los ejercicios más fáciles son donde los ciclos son obvios.
    - **for** tiene una condición/instrucción a evaluarse/cumplirse, y mientras que sea true dicha condición continuará, hasta que sea false.
    - **break** indica que cuando se encuentre esa instrucción se acaba el ciclo.
    - **continue** continua la interacción actual hasta que se pase a la siguiente.
    - A diferencia del **for** que se ejecuta hasta que se define, el **while** se ejecuta hasta que la expresión booleana lo decide.
    - **dowhile** es igual al **while** a diferencia que la condición se evalúa después de que se ejecuta al menos una vez el bloque de instrucciones. ****
- undefined, null y NaN.

## Parte 3

- 

## Parte 4

- 

## Parte 5

-