# notas profesion de javascreipt CF

## Sean benebolos, son notas personales que no pense que fuera a compartir, ademas son tomadas al vuelo por ello puede que tenga errores de sintaxis o problemas de ortografia.

## Validar un bo0leano

- let booleano = new Boolean("false");
- consol.log(booleano.toString());
- valores booleanos pordefecto falsos
  - undefined
  - NaN
  - null
  - 0
  - .0
  - ""
  - false

## ciclos

- for ejecuta una instrucion hasta que el valor de la instruccion cumpla una condicion es pesifica
  - ```
    for(let i = 0; i <=10; i++){
      console.log(i);
      }
    ```
  - break rompe el ciclo (sale del ciclo)
  - ```
    for(let i = 1; i <=10; i++){
      console.log(i);
      if(i==5) break;
      }
    ```
  - Continue indica que se debe romper el ciclo actual y pasar a la siguiente iteracion del ciclo
  - ```
    for(let i = 1; i <=10; i++){
      if(i%2) continue;
      console.log(i);
      }
    ```

## Funciones

- imaginar como entrada => proceso => salida
- se definen con la palabra "function" seguido del nombre de la funcion y el listado de parametros (o ninguno) entre parentesis seguido de llaves, tambien hay funciones anonimas (lamdas)
  - function nameFunction () {}
  - ```
    // Creo una funcion que retorna el cuadrado de un numero
    function cuadradoDeNumero (numero) {
      return numero * numero
    }
    // asigno lo que retorna la funcion a una variable
    let cuadrado_de_numero = cuadradoDeNumero(3)
    console.log(cuadrado_de_numero)
    ```
  ````
  - ```
  function(){}
  ````
- se utiliza la palabra reservada "return" para retornar el la salida de la funcion
- cuando no utilizamos return en una funcion, la salida de dicha funcion sera "undefined"
- cuando se llega a la palabra retur el flujo de ejecucion de la funcion es terminado, osea que todo lo que este despues de dicha palabgra en el flujo es ignorado
- ### scope

  - var, es utilizado para declarar una variblable que debera tener como scope el scope local de la funcion donde fue declarada
  - let, es utilizado para declarar una variblable, esta a diferencia de var su scope solo es local al bloque donde fue llamada.
  - const, es utilizado para declarar un valor constante o que no cambia en el flujo de ejecucion
  - ```
      function validarEdad(edad) {
      // definiremos la variable "var resultado" en un bloque del ciclo if y esta variable tendra como scope (podra ser llamada) desde fuera del este bloque donde fue declarada (scope de funcion)
      if (edad >=18 ){
        var resultado = "eres mayor de edad";
      }else{
        var resultado = "eres menor de edad";
      }
      console.log(resultado)
      }
      validarEdad()
    ```
  - ```
      function validarEdad(edad) {
      // definiremos la variable "let resultado" en un bloque del ciclo if y esta variable tendra como scope (podra ser llamada) solo el bloque donde fue declarada
      if (edad >=18 ){
        let resultado = "eres mayor de edad";
      }else{
        let resultado = "eres menor de edad";
      }
      console.log(resultado)
      }
      validarEdad()
    ```
  - dado el caso necesitemos utiizar una variable de tipo let en una funcion como la anterior podemos declararla antes del ciclo para que esta este disponible a nivel de la funcion
  - ```
      function validarEdad(edad) {
      // Declararemos la variable "let resultado" a nivel de la funcion lo cual le permitira se tener un scope local en toda la funcion
      let resultado
      if (edad >=18 ){
        resultado = "eres mayor de edad";
      }else{
        resultado = "eres menor de edad";
      }
      console.log(resultado)
      }
      validarEdad()
    ```

- ## Parametros y Argumentos

  - Los arguemntos llenan los parametros
    - ```
      function nameFunction(estoEsUnParametro) {}
      nameFunction(estoEsUnArgumento)
      ```
  - Argumentos, son los valoses enviados cuando llamamos la funciona
  - Parametros, es la variable que colocamos en la definicion de la funcion, una funcion puede tener o no tener parametros, puede existir parametros por defecto u recibir muchos parametros que no son asignados (para esto se utriliza el objeto arguments).

    - los parametros no tienen tipo, por tanto reciben argumetos de cualquier tipo que sea enviado desde el llamado de la funcion
    - no se rebisa la cantidad de parametros enviados (pedes enviar menos o mas argumentos cuando llamas la funcion)
    - cuando tenemos un parametro que no resibe un argumento el valor de este en la ejecucion del codigo es "undefined"
      - ```
        function cuadrado(numero) {
          console.log(numero)
        }
        cuadrado()
        ```
    - Cuando el parametro es necesario para la ejecucion de la funcion podemos recurrir a dos posibilidades, una estableser un valor por defecto para ese parametro (el cual es asignado cuando no se envia el argumento al llamar la funcion), o en la ejecucion de la misma informar al usuario que es necesario dicho parametro
      - Los parametros con valores por defecto deben ir despues de los parametros sin valores por defecto.
        - ```
          function cuadrado(numero, numero2 = 10) {
            console.log(numero);
            console.log(numero2);
            if (numero == undefined){return console.log("no a definido un numero");}
            console.log(numero)
          }
          cuadrado()
          ```
      - Podemos enviar tantos argumento como deseemos a una funcion que no tenga definidos parametros, para acceder dichos argunentos podemos utilizar el objeto arguments.
        - ```
          function cuadrado() {
            console.log(arguments[0])
            console.log(arguments[1])
            console.log(arguments[2])
            let vsuma = arguments[0] + arguments[1] + arguments[2]
            console.log("suma de argumentos (valores 1,2,3)  = " + vsuma);
          }
          cuadrado(1,2,3,4,5,6,7,8,9,10)
          ```

## Funciones anonimas

- En programacion decimos que cuando un tipo de dato puede ser asignado a una variable, retornado o enviado com argumento, es un ciudadano de primer nivel (first class citizen), es normal que en un lenguaje los numeros, las cadenas e incluso los conseptos sean de este tipo, lo que no es tan normal es que tambien digamos ello de la funciones, en javascript tambien podemos hacer esto con una funcion, por lo general se conocen como funciones anonimas.
- Las funciones se pueden asignar a variables, enviar como argumentos e incluso las funciones pueden retornar otras funciones!
  - ```
    // Vamos a retornar una funcion desde otra funcion, pasando la segunda a la primera como argumento.
    function executor(laFuncionASerLlamada){
      laFuncionASerLlamada();
    }
    function llamadaDesdeOtraFuncion(){
      console.log("Me han llamado desde otra funcion")
    }
    executor(llamadaDesdeOtraFuncion)
    ```
  - ```
    // Este codigo hace lo mismo que el anterior pero es mas comun encontrar este tipo de estructuras que la anterior.
    function executor(laFuncionASerLlamada){
          laFuncionASerLlamada();
        }
    executor(function(){
          console.log("Me han llamado desde otra funcion");
        });
    ```

## Contexto (dificil de entender cuando cambia de lugar)

- El valor "this." representa el codigo que se esta ejecutanto en ese momento, el valor de this cambia dependiendo el que parte del codigo nos encontramos al valor de esta variable "this." se le conoce como contexto, en javascrip el contexto es flexible y muy dinamico, esto tiene sus pros y sus contras.
  - siempre el contexto sera el objeto que mande llamar la funcion
  - podemos cambiar de paradigma de desarrollo utilizando el mismo lenguaje
  - podemos implementar distintos de patrons de diseño con mucha facilidad
  - trae tambien confuncion respecto al valor que tiene "this"
    - como cambia
    - como reasignarlo
    - como se puede conservar para que no cambie su valor
- ```
  console.log(this);
  function demo(){console.log(this);}
  demo();
  ```

## Arrow funtion

- En javascript existe otra firma de definir funciones comunmente conocida como arrow functions

  - Reciben el nombre de la variable que las contiene
  - las llaves {} pueden omitirce si es que son solo de una line
  - cuando la funcion es solo de una linea, dicha linea es la que se retorna por ente no es necesario declarar retono de dicha funcion
  - ```
    // estas funciones reciben el nombre de la variable que las almacena para este caso la funcion se llama "demo"
    let demo = () =>{
      console.log("hola mundo");
    }
    demo()
    ```
  - ```
    // Pueden existir funciones anonismas (sin nombre)
    ()=>{console.log("Hola mundo");}
    ```
  - ```
    // en funciones de una linea no es necesaria la palabra return ni las llaves
    let nombreDeLaFuncion = ()=> console.log("Hola mundo");
    nombreDeLaFuncion()
    ```
  - ```
    // Estas dos funciones hacen lo mismo
    function suma(a,b){
      return a+b;
    }
    console.log(suma(5,1));

    // es la misma fucion de arriba
    suma = (a+b)=> a+b;
    console.log(suma(5,1));
    ```

- Las arrow function se utilizan cuando no queremos cambiar los valores de los contextos

  - ```
    // debido al contexto de setTimeout el valor las variables cambia a undefined
    let tutor = {
      name: "Victor",
      lastname: "Franco",
      language: "javascript",
      nameFullAndSpeciality: function(){
        setTimeout(function(){
          console.log(this.name + " " + this.lastname + ", especialidad " + this.language);
        }, 1000);
      }
    }
    tutor.nameFullAndSpeciality();
    ```
  - Cada vez que se envie una funcion como argumento a otra funcion y se requiera conservar el valor de this, en este caso se debe utilizar la sintaxis de la flecha para que este no mute en el flujo, osea el contexto no se reasigna.
  - ```
    // cuando utilizamos una arrow function para conservar el valor del contecto a setTimeout el valor las variables no cambia y sigue siendo el que tiene el objeto
    let tutor = {
      name: "Victor",
      lastname: "Franco",
      language: "javascript",
      nameFullAndSpeciality: function(){
        setTimeout(()=>{
          console.log(this.name + " " + this.lastname + ", especialidad " + this.language);
        }, 1000);
      }
    }
    tutor.nameFullAndSpeciality();
    ```

### Modificar el contexto Call, Aply, Bind

- javascript tiene metodos para asignar el valor que nosotros queramos al contexto (this) dichos metodos son bind(), call(), apply(), esto nos permite asegurar que this apunta al objeto que queremos para que este modifique el contexto de la funcion, recuerden que el contexto de una funcion es "desde donde llamamos dicha funcion \<this.>" y por tanto si no aseguramos el contexto que necesitamos, pueda que no podamos acceder a los valores solicitados (por la funcion que hace el llamado) donde debemos extraer dichos valores.
- Recreemos el error que podemos obtener sera "undefined" para los valores que estemos accediendo

  - ```
    //para simular este error utilizaremos una funcion a la que le pasamos otra funcion como parametro
    function executor(funcionASerLlamada){
      funcionASerLlamada();
    }
    let tutor = {
      name: "Victor",
      lastname: "franco",
      fullname: function(){
        console.log(this.name + " " + this.lastname);
      }
    }
    executor(tutor.fullname)
    // la salida de esta funcion sera "undefined", esto se debe a que el contexto (donde es llamada la funcion) es executor y en este punto "this" es reasignado y este no tiene acceso a la variable tutor

    // si hacemos el llamado desde el objeto no hay dicho problema
    tutor.fullname()
    ```

  - ```
    // podemos incluso utilizar la funcion arrow para intentar no modificar el contexto, pero dicha solucion no nos servira debido a que el contexto se esta modificando en la funcion executor
    function executor(funcionASerLlamada){
      funcionASerLlamada();
    }
    let tutor = {
      name: "Victor",
      lastname: "franco",
      fullname: ()=>{
        console.log(this.name + " " + this.lastname);
      }
    }
    executor(tutor.fullname);
    tutor.fullname();
    ```

- Como solucionamos dicho error implementando las funciones bind(), call(), apply(), separemos estas funciones segun su tiempo de ejecucion

  - 1. asignar el valor de this y llaman la funcion de manera imendiata (call y aply)

    - ```
      // en este caso para la solucion utilizaremos la funcion call, no podemos utilizar las function arrow con la funcion call
      // asignaremos el valor tutor a la funcion call
      function executor(funcionASerLlamada){
        funcionASerLlamada.call(tutor);
      }
      let tutor = {
        name: "Victor",
        lastname: "franco",
        fullname: function(){
          console.log(this.name + " " + this.lastname);
        }
      }
      executor(tutor.fullname);
      tutor.fullname();

      // podemos luego de ello utilizar la funcion call para hacer otros llamados
      function greets(name1){console.log("hola " + name1);}
      greets.call(window, "Uriel");

      ```

    - ```
      // en este caso para la solucion utilizaremos la funcion aply, es igual a la primera solo que a diferencia de esta los argumentos se envian en un arreglo, ose son lo mismo.
      function executor(funcionASerLlamada){
        funcionASerLlamada.aply(tutor);
      }
      let tutor = {
        name: "Victor",
        lastname: "franco",
        fullname: function(){
          console.log(this.name + " " + this.lastname);
        }
      }
      executor(tutor.fullname);
      tutor.fullname();

      // podemos luego de ello utilizar la funcion call para hacer otros llamados
      function greets(name1){console.log("hola " + name1);}
      greets.aply(window, ["Uriel"]);

      ```

  - 2. los que construyen una funcion que puede ejecutarce despues(bind)

    - no tiene mucho sentido utilizar una funcion en la cual sacrificamos su dinamismo (pues tenemos que pasar la variable tutor, modificamos el contexto para que sea tutor), con esto en mente podemos utilizar la funcion bind(), de echo es una mejor herramienta para solucionar el problema del executor (funcion arriba)
    - bind() tiene definido de antemano quien sera "this" antes de ejecutarce, cual es su contexto y portanto no cambiara
    - ```
      // simplemente en el llamado de la funcion executor al argumento le adicionamos el metodo bind() con el contexto que deseemos modificar
      function executor(funcionASerLlamada){
        funcionASerLlamada();
      }
      let tutor = {
        name: "Victor",
        lastname: "franco",
        fullname: function(){
          console.log(this.name + " " + this.lastname);
        }
      }
      executor(tutor.fullname.bind(tutor));

      ```

## Arreglos

- es una lista de elemento que puede ser multidimencional y la cualcomienza en 0
- ```
  // recorre un arreglo con un ciclo for
  let arreglo = [12,42,35,49,51,6]
  for (let i= 0; i < arreglo.length; i++){
    console.log("valor almacenado en la posicion " + i + " : " + arreglo[i]);
    let elemento = arreglo[i]
    console.log("multiplicando el elemento: " + (elemento * elemento));
  }
  ```
- ### Metodos

  - ```
    // recorrer arreglos con forEach
    let languages = ["ruby","javascript","python","php"];
    languages.forEach(function(element){
      console.log(element);
    });
    ```
  - ```
    // filtrar elementos de un arreglo (crea un arreglo nuevo)
    let languages = ["ruby","javascript","python","php"];

    languages_validates = languages.filter(function(element){
      return element  != "ruby";
    });

    languages_validates.forEach(function(element){
      console.log(element);
    });
    ```

  - ```
    // filtrar elementos de un arreglo (crea un arreglo nuevo), con funcion arrow
    let languages = ["ruby","javascript","python","php"];

    languages_validates = languages.filter((element)=> element != "ruby");

    languages_validates.forEach(function(element){
    console.log(element);
    });
    ```

  - ```
    // buscar un elemento en un arreglo, con funcion arrow
    let languages = ["ruby","javascript","python","php"];

    look_element = languages.find(element => element == "javascript");

    console.log(look_element);
    ```

  - ```
    // map crea un arreglo nuevo con el retorno de la funcion que estamos invocando
    let numbers = [10,15,4,11,3,25,5];
    cuadradoDeNumbers =  numbers.map(number => number * number);
    console.log(cuadradoDeNumbers);

    // en este caso recorremos el arreglo y convertimos los string en numeros, los cuales son addicionados a un nuevo arreglo
    let stringNumbers = ["10","5","4","11","3","2","5"];
    stringToInteger =  stringNumbers.map(number => parseInt(number));
    console.log(stringToInteger);
    ```

## Objetos

- las clases no exisqten en javascript
- javascript object notation
- van entre {} (llaves)
- ```
  let course = {
    title: 'curso profesional de javascript',
    duration: 2.2,
    format: 'video',
    block: ['introduction', 'functions']
  }
  ```
- se pueden leer de dos formas como objeto o como si fuera parte de un arreglo (llamando el valor por la clave)
  - ```
    let course = {
      title: 'curso profesional de javascript',
      duration: 2.2,
      format: 'video',
      block: ['introduction', 'functions'],
      inscription: function(user){
        console.log(user + " ahora esta inscrito");
      }
    }
    console.log(course.title);
    console.log(course['title']);
    course.inscription('vifrac');
    ```
- se pueden reasignar pasando el argumento a la funcion que estamos definiendo como objeto
  - ```
    let course = {
      title: 'curso profesional de javascript',
      duration: 2.2,
      format: 'video',
      block: ['introduction', 'functions'],
      inscription: function(user){
        console.log(user + " ahora esta inscrito");
      }
    }
    console.log(course.title);
    course.title = 'Curso basico de javascript'
    console.log(course.title);
    ```
- funciones constructoras
  - haremos el mismo ehemplo pero con una funcion constructora
  - por convencion van con la primera letra en mayusculas per no es obligacion
  - ```
    function Curso(title){
      this.title = title
      this.inscription = function(user){
        console.log("se inscribio el usuario " + user)
      }
    }
    let cursoJavascript = new Curso("cursos profesional de javascript");
    cursoJavascript.inscription("victor")
    ```

## Clases

- fueron introducidad en las ultimas versiones, las encontraras como

  - no requiere la palabra reservada funtion para los metodos u function arrows
  - tienen un metodo contructor para dotar de propiedades a la clase
  - ```
    // con class declaration
    class Curso{}

    // con class expresion
    let Curso = class{}
    let Usuario = class Usuario{}
    ```

  - ```
    class Curso{
      constructor(title){
        this.title = title
      }

      inscription(user){
        console.log(user + " se ha inscrito");
      }
    }
    let javascripCurso = new Curso("Nuevo curso de javascript");
    console.log(javascripCurso.title)
    javascripCurso.inscription("vifrac");
    ```

## Herencia

- la herencia se implementa con la parabra reservada "extends" y el nombre de la clase padre
- las clases pueden heredar del buildingObject (objetos por defecto de javascrip) con el fin de personalizar o especializar dichos usos!
- puede heredarse de funciones constructoras
- sobreescritura de metodos, a los metodos que son heredados del padre se les puede dotar de funcionalidades espesificas en el hijo, osea se sobrescribe el metodo padre en el hijo

- ```
  // ejemplo de herencia para un video
  // Implementacion de la calse padre
  class Player{
    play(){ this.video.play(); }
    duration(){ return this.video.duration / 100; }
  }

  // implementacion de dos clases de videos que asu vez heredan de player
  class Vimeo extends Player{
    open(){ this.redirectToVimeo(this.video);}
  }
  class Youtube extends Player{
    open(){ this.redirecToYouTube(this.video);}
  }
  let video_vimeo = new Vimeo()
  video_vimeo.open("video)

  ```

- ```
  //herencia de una funcion constructora
  function User(){}
  class Admin extends User{}

  // herencia desde buildingOnjects
  class CustomDate extends Date{}
  class CustosArray extends Array{}
  ```

- ```
  //Sobreescribir metodos
  class User{
    constructor(name){
      this.name = name;
    }
    greats(){
      console.log("Hola usuario " + this.name);
    }
  }

  // sobreescribimos el metodo del padre "greats"
  // Tenemos acceso a los metodos del padre con la palabra reservada super
  // Tambien podemos acceder a la funcion constructora del padre igual con la palabra reservada super() y entre parentesis le pasamos los argumentos que necesite el constructor
  class Admin extends User{
    constructor(name){
      super(name);
    }
    greats(){
      console.log("Hola usuario local");
      super.greats();
      console.log("Este es el panel administrativo")
    }
  }
  let admin = new Admin("vifrac");
  admin.greats();
  ```

## abstraccion

- encapsulacion, nos provee una estrategia de abstrapcion donde podemos interactuar con las propiedades de un objeto a partir de los metodos del mismo objeto.
- por lo general utilizamos metodos accesores para modificar y leer las propiedades de un objeto
- recreemos unos de los problemas que ocurren cuando acedemos directamente a la propiedad del objeto para que esta sea cambiada,esto viola el principio de encapsulacion.
- utiliza un guion bajo en el nombre de la propiedad, porque no puedes llamar a una propiedad de la misma forma que el metodo.
- a los setters se les debe pasar 1 argumento y solo uno, no 0 ni tampoco mas de 1.
- in el interior los setters y getters se comportan como si estuvieremos modificando la propiedada, pero en realidad hay un metodo que se encarga de ello
  - ```
    //Utilizaremos la propiedad name para cambiar el dato que es almacenado en ella (nombre), imaginemos que esta propiedad (name) se modificara por nombre, dichos cambios es necesario hacerlos en todas las partes donde hacemos uso de dicha propiedad.
    class CreateUser{
      constructor(name){this.name = name;}
    }
    let user = new CreateUser("Marcos");
    console.log(user.name);
    user.name = "victor";
    console.log(user.name);
    ```
  - ```
    // Como corregirlo el problema anterio con encapsulamiento y un getter.
    class CreateUser{
      constructor(name){this._name = name;}
      get name(){
        return this._name.charAt(0).toUpperCase() + this._name.slice(1);
      }
      set name(name){
        this._name = name;
      }
    }
    let user = new CreateUser("marcos");
    console.log(user.name);
    user.name = "victor";
    console.log(user.name);
    ```

## metodos estaticos o metodos de clase

- no necesitan ser llamados por un objeto una instancia de la clase
- estan presedicos (llevan antes) la palabra static
- ```
  class User{
    static createUser{// logica }
  }
  User.createUser
  ```
- ```
  class User{
    constructor(permisos="lectura"){ this._permisos = permisos; }
    static createAdmin(){
      let user = new User("Administrador");
      return console.log(user._permisos);
    }
  }
  let administrador = User.createAdmin();
  ```

## lenguaje orientado a prototipos

- no existen clases como tal, javascript implementa un azucar sintactico de clases pero estas son transpiladas a protipos
- creacion de un onjeto

  - \_\_proto\_\_
  - ```
    let user = {nombre: "victor"}
    ```
  - Creemos un objeto apartir de prototipos y verifiquemos sus metodos y atributos
  - para crear un objeto debemos pasar como argumento el prototipo del cual hereda (object es la raiz de todos), si lo pasamos null el prototipo sera vacio.
  - hay que tener en cuenta que la herencia aqui se maneja como una cadena de prototipos, osea el interprete de javascript 1. busca el metodo en el objeto perro, si no lo encuentra 2. pasa a buscarlo en sus prototipo, es decir sus objeto padre (apartir del cual se creo el perro) si lo encuetra lo ejecuata, 3 .sino continua buscando en el prototipo del padre, y asi sucesivamente, a esto se le conoce como cadena de prototipos, 4. esta cadena se acaba cuando el la busqueda se topa con un objeto cuyo prototipo sea null, como nuestro caso (animal) 5. cuando el protpotipo sea nulo y no se a encontrado el metodo o la propiedad el valor retornado sera "undefned"
  - ```
    //creemos un objeto a partir de un prototipo pero este sera vacio, por ello mandamos como prototipo "null"
    let animal = Object.create(null);

    //podemos adicionar atributos
    animal.vivo = true;

    //podemos adicionar metodos al objeto animal
    animal.estaVivo = function(){if(this.vivo) console.log("esta vivo");}

    //podemos crear objetos apartir del prototipo animal, los cuales heradaran sus atributos y funciones com si se tratare de una instancia de una clase
    let perro = Object.create(animal);
    perro.estaVivo();

    // si buscamos una propiedad que no este en el prototipo del perro o sus objetos antesesores antesesores se retornara undefined
    console.log(perro.edad);
    ```

  ## la propiedad prototype

  - la funcion "prototype" es igual a \_\_proto\_\_
  - podemos decir que el prototype de una funcion pasa a ser el prototipo de los objetos creados con dicha funcion
  - podemos utilizar esta propiedad de la funciones para modificar los objetos creados por las funciones incluso despued de haber sido creados, eso quiere decir que cuando creamos una nuevo atributo con la propiedad "prototype" este hereda a todos los obnjetos creados a travez de dicha funcion.
  - ```
    //Funcion constrcutora de un objeto (base para entender el poder de prototype y parte del siguiente ejercicio)
    function User(){}
    user = new User();
    console.log(user.__proto__)
    console.log(User.prototype)
    console.log(user.__proto__ === User.prototype)

    // esta funcion no existe en este objeto.
    console.log()user.saludar
    ```

  - ```
    //Funcion constrcutora de un objeto (base para entender el poder de prototype y parte del siguiente ejercicio)
    function User(){}
    let user = new User();
    let victor = Object.create(user)

    User.prototype.saludar = function(){ console.log("ahora saludo");}
    // la funcion es probista al objeto despues de ser creado
    user.saludar();
    victor.saludar();
    ```

  - ```
    //aqui vamos a utilizar herencia para dotar a los objetos de nuevas funcionalidades
    function User(){}
    User.prototype.saludar = function(){ console.log("ahora saludo");}

    //creamos una nueva funcion que erede de user
    function Admin(){}
    Admin.prototype = new User();

    let victor = new Admin();

    victor.saludar();
    ```

## Programaion asincrona

- Callback, es una funcion que se le pasa a una operacion asincrona con la espectativa de que dicha funcion sera ejecutada cuando la opetacion termine, pero los callback tienen defectos.
- promesas, son una alternativa para mejorar prosesos asincronos en javascrip, usan una sintaxis mas clara y por diseño existen maneras para esperar un conjunto de procesos asincronos antes de ejecutar otra accion
  - las promesas con los callback
    - las promesas son un tipo de objeto en javascrip
    - no enviamos ninguna funcion como argumento, solo el string
    - sobre el resultado (un objeto de tipo promise) de la ejecucion del request (variable "rp" en el ejemplo) ejecutamos un el metodo "then" del objeto al cual le enviamos una funcion, dicha funcion se ejecutara si la promesa se ejecuro sin errores, ademas existe un metodo catch al cual le podemos enviar una funcion que se ejecutara si la promesa falla.
    - una promesa es un objeto que probablemente produsca un valor en el futuro, este valor puede ser el resultado de una operacion asincrona o un error de porque no se pudo completar alguna operacion.
    - las promesas usan callbacks
    - las promesas pueden estan en diferentes estados
      - fullfiled: la promesa se cumplio con exito
      - rejecte: la promesa no se cumplio con exito
      - pending: la promesa no se a cumplido, el estado de la promesa cuando la aoperacion no a terminado
      - setled, finalizada cuando la promesa termino con exito o con algun error
- ```
  // inplementacion de un callback con la libreria request
  const request = require("request");
  request("http://google.com", function () {
  console.log("termine la peticion de google");
  });
  console.log("yo voy despues en el codigo de la peticion a google");
  ```
- ```
  //implementacion de una promesa con las librerias request y request-promise
  const rp = require("request-promise");

  rp("http://google.com")
    .then(function (html) {
      console.log("termine la peticion a google");
    })
    .catch(function (err) {
      console.log(err);
    });
  console.log("yo voy despues en el codigo de la peticion a google");
  ```

- Retorno de promesas, una promesa representa un valor que eventualmente existira, el resultado de una operacion o el error que rechaso la promesa, esto nos permite que metodos asincronos retornen resultados como si fueran metodos sincronos.
  - el constructor "Promise" nos permire retornar promesas
  - para crear una promesa debemos pasarle al constructor (parametro que resibe la promesa) una una funcion a la que llamamos el executor, este a su vez recibe una funcion resolve y una funcion reject y pueden tener un nombre customizado, pero la convecion es resolve and reject.
    - resolve, la primera funcion, se debe mandar a llamar cuando la cuando la funcion asincrona termino y fue exitosa, ademas resibe como argumento el resultado que queremos enviar de la peticion asincrona y ademas marca la promesa como fullfiled o completada.
    - reject, la segunda funcion, marca la promesa como "reject", debe mandarse a llamar cuando hubo un error en al operacion asincrona y queremos hacer saber que la promesa no pudo completarse, la funcion debe recibir como argumento un error o una razon del porque no pudo cumplirse la promesa.
- la operacion asincrona debe ejecutarse dentro del executor
- para este caso utilizaremos request, recuerda que request utiliza callbaks (funcion de retorno) dicha funcion resibe dos argumento un error en caso de que algo haya salido mal en la opéracion asincrona y la respuesta del server en caso de haber leido la pagina de manera exitosa (err, response es notacion que normalmente tienen las librerias de node)
- aprovecharemos los resultados del callback para marcar la promesa como rechazada o como resuelta
  se verifica el error "if(err)" y si hay algunno se marca la promeza como rechazada, de locontrario como resuelta y se pasa la respuesta.
- luego utilizamos el metodo leer de forma asincrona

  - ```
    const request = require("request");

    function leer(url) {
    return new Promise(function (resolve, reject) {
    request(url, function (err, response) {
    if (err) {
    reject(err);
    } else {
    resolve(response);
    }
    });
    });
    }
    leer("http://vifrac.com")
    .then(function (response) {
    console.log(response);
    })
    .catch(function (err) {
    console.log(err);
    });
    ```

- Resolver multiples promesas

  - en muchas ocaciones para ejecutar un calculo o procesar un dato, usa callbacks para hacer esto nos podria acarrear problemas como funciones ilegibles, funciones dentro de otras funciones, para evitar esto existe el metodo statico en el objeto promiss
  - ```
    //validar multiples promesas
    let p1 = new Promise((resolve, reject) =>
      setTimeout(resolve, 500, "hola mundo")
    );
    let p2 = new Promise((resolve, reject) =>
      setTimeout(resolve, 600, "Segundo hola mundo")
    );
    let p3 = Promise.reject();

    let saluda = () => console.log("Hola a todos");
    p1.then(function () {
      p2.then(function () {
        saluda();
      });
    });

    Promise.all([p1, p2, p3])
      .then((resultados) => {
        console.log(resultados);
        saluda();
      })
      .catch(() => console.log("falle :("));
    ```

  - en una cadena de promesas el resultado de la primera es enviado al llamado de la segunda como argumento.
  - ```
    // esto sera una cadena de promesas el valor retornado en la primera funcion (calcular) es enviado a la segunda como un argumento (sin los parentesis, sicolocamos los parentesis nos ejecutara la funcion y el valor de retorno), y el valor de retorno de la segunda funcion es impreso mediante el console.log del tercer then.
    // notese que le pasamos la segunda promesa como una funcion, esta a su vez es ciudadano de primer nivel, pero tambien el resultado de la primera es enviado como argumenro a la segunda, pasa lo mismo cuando al finalizar enviamos el consol.log (como metodo de funcion) y este toma como argumento el resultado de la anterior promesa.
    function calcular() {
      return new Promise((resolve, reject) => {
        setTimeout(resolve, 400, 5);
      });
    }
    function segundoCalculado(numero) {
      console.log(numero);
      return new Promise((resolve, reject) => {
        setTimeout(resolve, 200, "segunda promesa");
      });
    }

    calcular().then(segundoCalculado).then(console.log);
    ```

## Spread Operator

- sintaxis de propagacion o express sintax, nos permite expandir un arreglo o un objeto para usar sus elementos, como argumentos de una una funcion, para conbinar erreglos o para combinar hashes, segun sea el caso
- el operador son 3 puntos \<...>
- para el siguente ejemplo [2, 3, 5] sera algo asi 2,3,5
- se puede utilizar cuando queremos combinar dos arreglos

- ```
  let numbers = [2, 3, 5];
  function sumar(n1, n2, n3) {
    return n1 + n2 + n3;
  }
  //funcion de aply le pasamos los datos al vañlor mediante el segundo argumento de apply
  let resultado = sumar.apply(this, numbers);

  // operador de propagacion
  let resultado1 = sumar(...numbers);

  console.log(resultado);
  console.log(resultado1);

  ```

- ```
  // aahora utilizaremos el operador de propagacion para unir arreglos
  let numbers = [2, 3, 5];
  let otherArray = ["hola", "mundo"];
  console.log([...numbers, ...otherArray]);
  console.log([1,7,9 ...numbers, ...otherArray, 11, 55, 4]);

  ```

- ```
  // unir objetos con el operador de propagacion
  let obj = {
    valor: 1,
  };

  let obj2 = {
    valorOtro: 2,
  };
  console.log(obj);
  console.log(obj2);

  let joinObjs = {
    ...obj,
    ...obj2,
  };

  console.log(joinObjs);


  ```

## ciclos for of y for in

- el ciclo for of puede aplicarse sobre cualquier objeto iterable, un objeto iterable puede ser un arreglo, una cadena, o algunos tipos de objetos como map o sise.
  - Itera los valores
  - en cada iteracion nos entrega un elemento del iterable
  - no posee index
- ```
  // iterar elementos con for of
  let arr = [2, 3, 5];
  for (element of arr) {
  console.log(element);
  }
  ```
- ```
  // validamos una funcion a la que queremos operar cada uno de sus argumentos
  function greet() {
    for (element of arguments) {
      console.log("hola " + element);
    }
  }

  greet("Victor", "Manuel", "Franco", "Cañon");

  ```

- el ciclo for in, itera las propiedades y nos entrega las mismas
  - solo muestra las propiedades iterables , (\_\_proto\_\_) proto no es una propiedada iterable.
- ```
  // Iterar las propiedades de un objeto, estraer
  let victor = {
    nombre: "victor manuel",
    edad: 23,
  };

  for (element in victor) {
    console.log(element);
  }

  ```

## Funciones asincronas

- async
  - las funciones asincronas se declaran siempre antes de de la funcion con la palabra async
  - siempre retornan una promesa, sin inportar el cuerpo de la funcion o el valor de retorno de la misma
  - algunas funciones explisitamente retornan una promesa
  - puedes utilizar en el cuerpo de la funcion "await"
- await
  - hace que la ejecucion del codigo espere a que una promesa sea resulta, evitando que uno deba escribir then o que constantemente tengas que crear funciones anonimas para el manejo de una promesa
  - solo se debe manejar con promesas
- ```
  //funcion asincrona (RETORNA UN APROMESA)
  async function pluss(n1, n2) {
    return n1 + n2;
  }
  // funcion asincrona que explisitamente retorna una promesa
  async function calculate() {
    return new Promise((resolve, reject) => {
      setTimeout(resolve, 400, 5);
    });
  }
  ```
- ```

  //manejo de una promesa con el metodo then
  let promesa = new Promise((resolve, reject) => {
    setTimeout(resolve, 400, 5);
  });

  promesa.then((resultado) => {
    console.log(resultado);
  });

  // manejo de la misma promesa con await, recuerda que la palabra reservada await solo puede utilizarce en una funcion asincrona
  (async function () {
    let promesa1 = await new Promise((resolve, reject) => {
      setTimeout(resolve, 400, 5);
    });
    console.log(promesa1);
  })();

  // mismo ejemplo anterior pero operaremos los valores que retornados por las promesas
  (async function () {
    let resultadoPromesa = await new Promise((resolve, reject) => {
      setTimeout(resolve, 400, 5);
    });
    let resultadoPromesa2 = await new Promise((resolve, reject) => {
      setTimeout(resolve, 400, 15);
    });
    console.log(resultadoPromesa + resultadoPromesa2);
  })();
  ```

- ```
  const fetch = require("node-fetch");

  // ejemplo practico de lo exlicado arriba con una peticion de mis repos a github
  async function showGitHubInfo() {
    let response = await fetch("https://api.github.com/users/vifrac/repos");
    let repos = await response.json();
    console.log(repos);
  }
  showGitHubInfo();
  ```

## Manejar errores en promesas

- para manejar errores debemos utilizar los bloques try and catch
- en async y await nos retona un objeto, no se puede capturar error como se hace con las promesas normales, lo debemos hacer con los bloques try y catch
- si hay mas de una promesa en el bloque try y esta falla enviara los valores al catch
- ```
  // como se cachea una promesa (control de errores)
  // promesa.then(()=>{/* resolve */}).catch((err)=>{console.log(err)});

  // como debemos hacerlo cuando utilizamos async y await, recuerda que en una promesa si una falla todas fallan, si es que ahy mas de una como en el ejemplo

  (async function () {
    try {
      let promesa1 = await Promise.resolve("Este es el error ...");
      let promesa2 = await Promise.reject("Este es el error de la promesa 2...");
      let promesa3 = await Promise.reject("Este es el error de la promesa 3...");
    } catch (err) {
      console.log(err);
    }
  })();

  ```

## modulos en javascript

- Es un apractica recomendada que los archivos de javascript que son modulos tengan la extencion _.mjs, aunque no hay diferencia interna en entre _.mjs y \*.js
- UN modulo se distingue de un archivo normal porque importa o exporta codigo

  - se debe utilizar la palabra reservada "export" para exportar el codigo
  - para importar codigo se deb utilizar la palabra reservada import y esta asu vez se compone de dos partes, los elementos que vamos a importar y el spesifaier que indica la url de donde se extrae dicho elemento
    - import { name } from './modulo_dos.mjs'
  - debe siempre existir un modulo de entrada desde donde se van a comenzar a cargar los modulos, osea a partir del cual se van a comenzar a leer los modulos
  - si utilizamos html debemos indicar que es un modulo en el script de carga
    - \<script src="./modulo_base.js" type='module'></script>
  - Cuando edxportamos valores de un modulo le estamos asignando un indicador que se usara al momento de iportar cada uno en otro modulo
  - podemos asignar un nombre por defecto al modulo

    - un mismo modulo puede exportar multiples valores por nombre pero solo puede exoprtar uno por default
    - se puede exportar cualquier expresion (resiltado de la exprecion es lo que se exportara) por defecto (validables, funciones, clases)
    - se c reara una variable con el valor por defecto que indicamos y en esta se almacenara los datos que son resuleltos
    - con llaves se traen lo nombres que solicitemos del modulo
    - sin llaves se trae el unico el unico valor por defecto.
    - ```
      // en el modulo de exportacion
      let valorPorDefecto = "Nuevo mundo";
      export default valorPorDefecto;

      // ene l modulo de importacion (def es un valor customizado puede ser cualquiera)
      // import def, {name} from "./modulo_dos.mjs";
      import def from "./modulo_dos.mjs";
      console.log(def);
      ```

  - (ReadOnly imports) no podemos modificar los valores que importamos de otro modulo
  - una variable exportada puede cambiar su valor desde dentro del modulo pero no fuerta de el u reasignar su valo

## Generadores e Iteradores

- estos sirven para almacenar una porcion de las colecciones de datos e iterar esta, dichas practica nos da buenos resultados en cuanto a rendimiento.
- Iterador

  - es cualquier elemento que implementa el itereator protocol, cualquier objeto que implemente un metodo(funcion) next que retorne un objeto con una propiedad value y una propiedad done implemeta el protocolo y por lo tanto es un iterador
  - objeto que implemementa metodo next
  - next es una funcion que retorna dos propiedades value y done
  - los iteradore y generadores nos permiten trabajar un dato a la vez
  - este datop a la vez es "value", osea lo que el iterador va producionedo, puede ser un numero, cadena, funciona.
  - la propiedad done es un bolleano que indica si el iterador a terminado de producir valores a iterar
    - cuando es "true" indica que el iterador se ha completado y no producira mas iteraciones
    - si es falso podemos segir iterando
  - se manda llamar con la funcion o metodo next del iterador (objeto creado)
    cuanto el iterador no cumple la condicion se envia como true
  - los valors se producen uno a la vez, no hay arreglos o estrcturas que almacene los datos
  - cada valor que se itera se va producionedo cuando llamamos next
  - la iteracion es peresosa, osea podemos mandar llamar la siguiente iteracion cuando queramos o no mandar llamar la siguiente iteracion
  - no hay forma de reiniciar el iterador, ademas de que solo se recorre una vez

  - ```
    // contrimos un iterador que imprime los numeros del 1 al  5
    let iterador = {
      currentValue: 1,
      next() {
        let result = { value: null, done: false };
        if (this.currentValue > 0 && this.currentValue <= 5) {
          result = { value: this.currentValue, done: false };
          this.currentValue += 1;
        } else {
          result = { done: true };
        }
        return result;
      },
    };

    // esta es una forma de llamar la funcion next
    console.log(iterador.next());
    console.log(iterador.next());
    console.log(iterador.next());
    console.log(iterador.next());
    console.log(iterador.next());
    console.log(iterador.next());
    console.log(iterador.next());

    // esta es otra forma de llamar la funcion next, no debara estar la anteroir forma en el mismo codigo, recuerde que solo se itera una vez sobre la variable current
    let item = iterador.next()
    while(!item.done){
      console.log(iterador.value);
      item = iterador.next()
    }

    ```

- Genreador

  - un generador en muchas cosas es parecido a un iterador aun que nos brinda una sintaxis mas clara y presiza, ademas que no necesitamos hacernos cargo del estado objeto

    - para producir un generador debemos contrir una funcion generadora, mismas que se reconocen por tener la palabra reservada fuction y al final un _ (function_), todas las funciones que se construyen con esta sintaxis retornan un generador
    - son algo como una funcion que se puede detener a media ejecucion para luego ser reanudadas en el mismo punto donde las dejamos
    - la funcion usa la palabra reservada yield, misma que se utiliza para parar la funcion y luego reanudarla en ese punto.
    - la llamar la funcion se crear el generador y explicitamente necesitamos pasar el metodo nex al objeto creado para que sea ejecudato.
    - cuando imprimimos el estado del objeto nos damos cuenta que es done, false y value 1
    - cuando enviamos mas impresiones de las que tiene la propieda value, dicha propiedad se cambia a undefined y el valor de donde pása a true
    - yield produce valores para el return, y aunque no lo mandamos llamar estos son retornados
    - si mandamos a llaamr return en una funcion generadora esta retornara el valor indicado como value y ademas terminara la iteracion, osea done: true, eso quiere decir que todo lo que este depued de un return no se ejecutara porque el iterable ya ha terminado
    - ```
      // funciones generadoras
      function* counter() {
        console.log("aqui estoy");
        yield 1;
        console.log("ahora estoy aqui");
        yield 2;
      }
      let generator = counter();
      //comentar la siguiente linea para ver el primer estado
      generator.next();

      //cuando imprimimos el estado del objeto nos damos cuenta que es done, false y value 1 el valor primer del yield

      console.log(generator.next());
      console.log(generator.next());
      ```

    - ```
      //este es el ejemplo del iterador anterior pero en formato generador
      function* counter() {
        for (var i = 1; i <= 5; i++) {
          console.log("estoy en el paso " + i);
          yield i;
        }
      }

      let generador = counter();

      console.log(generador.next());
      console.log(generador.next());
      console.log(generador.next());
      console.log(generador.next());
      console.log(generador.next());
      console.log(generador.next());
      console.log(generador.next());

      ```

    - ```
      //El return en una funcion generadora termina las iteraciones del y cambia done a true
      function* returnadora() {
        return 3;
        yield 5;
      }
      let g = returnadora();
      console.log(g.next());
      console.log(g.next());
      ```

  - delegar generadores

    - debido a que a yield podemos enviarle una funcion generadora y delegar la funcion de la continuidad del codigo a otro generador (generacion de delegadores) esto nos permite encadenar cuantos generadores queramos en la ejecucion de nuetro codigo
    - debemos colocar un _ fuego de yield y el nombre de la funcion generadora a delegar (yield_ counter())
    - ```
      //este es el ejemplo del iterador anterior pero en formato generador
      function* counter() {
        for (var i = 1; i <= 5; i++) {
          console.log("estoy en el paso " + i);
          yield i;
        }
      }

      //El return en una funcion generadora termina las iteraciones del y cambia done a true
      function* returnadora() {
        yield* counter();
        console.log("estoy de regresoa a la funcion returnadora");
        yield 9;
      }
      let g = returnadora();
      console.log(g.next());
      console.log(g.next());
      console.log(g.next());
      console.log(g.next());
      // recuerda que las supsecuentaes llamadas a counter las seguira manejando, returnadora y hasta que counter no termine de iterar no regresara a la iteracion propia de returnadora
      console.log(g.next());
      console.log(g.next());
      console.log(g.next());
      console.log(g.next());
      ```

- Simbolos

  - para retornar un simbolo usamos el constructor "Symbol()", el cual es un primitivo del lenguaje
  - lo que va dentro del "()" es solo una descripcion, no el elemento, un simbolo es un tipo de dato, como un boolean o una cadena
  - el valor del simbolo es el que esta guardado en una variable
  - cuando usar symbolos? en los iterables

    - ```
      // aunque dos simbolos tengan el mismo descrptor no son el mismo simbolo
      let simbolo = Symbol("mi-descriptor");
      let simbolo2 = Symbol("mi-descriptor");
      console.log(simbolo == simbolo2);

      let obj = {};
      obj[simbolo] = function () {
        console.log("la clave de mipropiedad es un simbolo");
      };
      obj[simbolo]();
      console.log(obj);

      let obj2 = {};
      obj2["name"] = function () {
        console.log("un simple obj");
      };
      obj2["name"]();
      console.log(obj2);
      ```

- Iterables con iteradores

  - los iterables nos permiten definir el comportamiento de uno de nuestros objetos cuando lo pasamos por un ciclo "for of" algunos ejemplos de iterables son los arreglos, las cadenas
  - el protocolo iterable nos permite definir cual va a ser el comportamiento de un objeto cuando es puesto en un ciclo for of
  - para que un objeto sea iterable necesita implementar un metodo que se llama "@@iterator", este metodo esta identificado en in objeto por un simbolo (no una cadena)

    - este (al igual que todos los ) simbolos no tiene un nombre por lo cual deberiamos pasar directamente el symbolo (@@iterator) para poder implemetar el metodo.
    - podemos encontrar el simbolo que representa "@@iterator" dentro de la constanete "Symbol.iterator, este tambien es conocido como "simbolos bien conocidos" o \<<well symbol>>
    - lo importante de este metodo (@@iterador) es
      - debe retornar un objeto "iterator" (no es el metodo... es un objeto)
        - las caracteriasticas del objeto iterator ya las conocemos
          - que tenga un metodo next()
          - que next retorne un objeto con las propiedades value y done... ya lo vimos arriba en en generadores e iteradores.
    - ```
      //esta es una funcion constructora
      function* counter() {
        for (var i = 1; i <= 5; i++) {
          console.log("estoy en el paso " + i);
          yield i;

          yield 6;
          console.log("estoy en el paso " + i + " en la segunda iteracion");
        }
      }
      //esta es una forma de ejecutar la funcion constructora, es neceario el .next()
      let generador = counter();

      //como podemos utilizar ciclo "for of" para iterar un generador
      for (numero of generador) {
        console.log(numero);
      }

      //un array de toda la vida y como se imprimen sus elementos
      let numeros = [2, 5, 10];
      for (numero of numeros) {
        console.log(numero);
      }

      //constante que representa un @@itetator o "simbolos bin conocidos <<well symbol>> "
      console.log(Symbol.iterator);
      ```

  - rangos

    - en otros lenguajes existe algunos objetos a los que llamamos rangos (ruby 1...100), no existen en javascript
    - a un rango le espesificamos un valor minimo y uno maximo
    - podemos iterar dentro de esos valores (min y max)
    - ```
      let rango = {
        min: null,
        max: null,
        cuerrentValue: null,
        //esta propiedad debe retornar un metodo next, como lo tenemos imblementado en el mismo objeto solo retornamos el mismo.
        [Symbol.iterator]() {
          return this;
        },
        next() {
          if (this.cuerrentValue == null) this.cuerrentValue = this.min;
          let result = {};
          if (this.cuerrentValue >= this.min && this.cuerrentValue <= this.max) {
            result = { value: this.cuerrentValue, done: false };
            this.cuerrentValue += 1;
          } else {
            result = { done: true };
          }
          return result;
        },
      };

      rango.min = 5;
      rango.max = 11;

      for (n of rango) {
        console.log(n);
      }
      ```

    - ```
      //mismo ejemplo anterior pero con un generador, no debemos manipular estados.
      let rango = {
        min: null,
        max: null,
        [Symbol.iterator]() {
          return this.generator();
        },
        generator: function* () {
          for (var i = this.min; i <= this.max; i++) {
            yield i;
          }
        },
      };

      rango.min = 1;
      rango.max = 10;

      for (n of rango) {
        console.log(n);
      }
      ```

## Cadenas

- existen dos versiones de cadenas un primitivo y un objeto, existen diferencias etre ambas, pero en terminos practicos son indistigibles a hora de programar.
  - primitivos son valores a los que no se les pueden asignar propiedades.
    - con comillas simples o dobles "", '' (let nombre = "manuel")
  - el medotdo "String() retorna un objeto del prototipo string (let name = String("manuel"))
  - cohercion de tipos, es cuando el lenguaje crea un objeto tenporal con el proposito de utilizar alguna propiedad o metodo, ejemplo con el primitivo string.length, esto no deberia poder hacerce porque es un primitivo y ellos no tienen propiedades, lo que hace javascript es generar un objeto temporal para utilizar el metodo length y caundo a obtenido el resultado del metodo elimina el objeto.
  - en javaescrip no existe diferencia entre usar comillas dobles o simples.
- caracteres especiales (skeiping = identificacion de caracteres especiales)

  - esto nos permite enviar instrucciones epeciales a la computadora, en una cadena nos permite mutar dicha cadena, con la barra invertida hacemos ello "\"
  - necesito escapar datos con parejas de comillas osea
    - escapar comillas ("hola \"mundo\"")
    - escapar comillas ('hola \'mundo\'')
    - no escapar comillas ('hola "mundo"'
    - no escapar comillas ("hola 'mundo'")
    - es utiliza para tabulaciones (\t) y saltos de linea (\n)

- concatenacion de caracteres (o cadenas) e interpolacion

  - concatenacion
    - console.log('hola' + 'mundo');
    - let a= "hola", let b = "mundo" console.log(a.concat(b));
  - interpolacion

    - son conocidos como template literal o template string
    - se definen entre backstrips (let nombre = "victor"; let template = `hola ${nombre}, ¿como estas? `; console.log(template);)
    - ```
      //algunos ejemplos de interpolacion
      let nombre = "victor";
      let template = `hola ${nombre}, ¿como estas? `;
      console.log(template);

      let number = prompt("Ingrese un mes de 1 a 12");
      let output = function (number) {
      if (isNaN(number) || parseInt(number) < 1 || parseInt(number) > 12) {
      console.log("Ingrese un mes de 1 a 12");
      } else {
      if (number.length >= 1 && number.length < 2) {
      console.log(`Mes 0${number}`);
      } else {
      console.log(number);
      }
      }
      // console.log(parseInt(number) >= 1);
      };
      output(number);

      console.log(number.padStart(2, "0"));
      console.log(number.padEnd(2, "0"));
      ```

## comparacion de strings

- cuando se comparan dos cadenas la comparacion de las dos cadenas se hace con los valores numericos de ambas por ello
  - console.log("A" > "B");
  - console.log("a" > "B");
  - console.log("a" > "A");
- hay unmetodo de comparacion de strings que nos arroja datos mas "esperados", es un metodo del objeto string el cual retornara un entero que puede ser -1,0,1
- existe inmutabilidad de cadenas por parte de los metodos, esos quiere dedir que un metodo como "toLowerCase" no mutara la cadena original, sino que mas bien creara una para realizar su labor y luego dicha cadena sera desechada.

  - ```
    // basic compare string
    console.log("A" > "B");
    console.log("a" > "B");

    // compare whith the method locale compare
    // 0, si son iguales las cadenas de comparacion
    console.log("A".localeCompare("A"));
    console.log("a".localeCompare("A"));

    // -1 retornara, Si la cadena base aparece antes que la cadena de comparacion "en orden alfabetico"
    console.log("A".localeCompare("Z"));
    console.log("a".localeCompare("Z"));

    // 1 retornara, Si la cadena de comparacion aparece antes que la cadena base "en orden alfabetico"
    console.log("Z".localeCompare("A"));
    console.log("z".localeCompare("A"));
    ```

- Una cadena esta compuesta por una secuencia de elementos (caracteres), eso quiere decir que el primer elemento de la cadena esta en la posicion 0 y asi sucesivamente
- se recomienda utilizar "for of" para iterar cadenas pues el ciclo for normal en ocaciones se rombien por caracteres unicode que trabaja dos valores por cada caracter

  - ```
    // iterar cadenas de string
    let word = "hola";
    let emogi = ":(";
    for (letter of word) {
      console.log(letter);
    }
    // eterando un emogi (utilizar un emogi)
    for (letter of emogi) {
      console.log(letter);
    }

    for (let i = 0; i <= emogi.length; i++) {
      console.log(emogi[i]);
    }

    ```

  - ```
    // iterar sobre porciones de una cadena con substring
    // imprime la palabra vida de la siguiente cadena
    // el ultimo caracter (13) no se imprime osea la funcion es excluyente
    let cadena = "hola mi vida es gradiosa";
    console.log(cadena.substring(7, 13));
    // se pueden invertir las posiciones para extraer datos.
    console.log(cadena.substring(17, 13));
    // no recibe valores negativos
    console.log(cadena.substring(-10));

    // iterar sobre porciones de una cadena con slice
    // lo mismo pero con slice
    console.log(cadena.slice(7, 13));
    // a diferencia que con substring, lo siguinte no es ejecutado debido aque la posicion start se encuentra antes que la end
    console.log(cadena.slice(17, 13));
    // recibe valores negativos
    console.log(cadena.slice(-5));
    ```

  - ```
    // busqueda de substyring en una cadena
    // se utiliza un algoritmo de comparacion de igualdades estricto
    // retorna la primera instancia de la coinsidencia
    // para el burcar las ultimas coindicencias, se debe utilizar el metodo "lastIndexOf"
    // lastIndexOf es mas lento que indexOf (porque debe recorrer todas las posiciones del elemento, para validar cual es la ultima)
    let cadena = "Hola vifrac";
    console.log(cadena.indexOf("vifrac"));
    console.log(cadena.indexOf("332132"));
    if (cadena.indexOf("vifrac") > 0) console.log("Encontrado");
    if (cadena.indexOf("332132") > 0) console.log("Encontrado");

    // podriamos hacer lo mismo con includes
    // includes usa un algoritmo de nombres "same value 0" (puede buscar un valor falsy como nan)
    // no retornaria la posicion, por el contrario si encuantra la cadena retorna true, de lo contrario false
    if (cadena.includes("vifrac")) console.log("Encontrado");
    if (cadena.includes("323232")) console.log("Encontrado");

    // Puedes validar inicios y finales de cadenas con los metodos endsWith y startWith
    let link = "https://vifrac.co";
    if (link.startsWith("https")) console.log("es un link seguro");
    if (link.endsWith("https")) console.log("es un link seguro");
    ```

  - ```
    // metodo esplit, convierte una cadena e una arreglo , utilizando un delimitador, este retornara un arreglo con las palabras separadas
    let texto = "estoy aprendiendo javascript con codigofacilito";
    let palabras = texto.split(" ");
    console.log(palabras);
    console.log(palabras.length);

    // el inverso de split es join, los une en un string
    console.log(palabras.join(","));

    //filtraremos marcas
    function filterWord(str) {
      let brand = ["codigofacilito", "javascript"];
      let wordFiltered = str.split(" ").map((word) => {
        return brand.includes(word) ? "XXX" : word;
      });
      console.log(wordFiltered.join(" "));
    }

    filterWord(texto);
    ```

  - ```
    // uso  de trim para remover elemtos en blanco
    let texto = " estoy aprendiendo javascript con codigofacilito ";
    console.log(texto.trimEnd());
    console.log(texto.trim());
    console.log(texto.trimStart());
    console.log(texto);

    //conocer la cantidad de codigos que tiene un string
    console.log(texto.length);

    // repite un string
    console.log(texto.repeat(10));

    // remplazar cadenas de texto
    console.log(texto.replace("javascript", "ruby"));
    ```

## Unicode

- el sistema unicode nos permite representar loa caracteres de una cadena como puntos de codigo, que a sus vez son traducidos par la computadora a bits (ensamblador), antes traducir los textos para que el usuario leyera un archivo era un desafio pues los caracteres que entiende la computadora no son los mismos que usamos nosotros
- va de los rangos desde u+0000 a u+0ffff
- ```
  // representacion unicode de algun caracter
  function toCodePoint(char) {
    var hex = char.charCodeAt(0).toString(16); //Convierte el caracter a hegxagesimal
    return "\\u" + "0000".substring(0, 4 - hex.length) + hex; //agrega los 0 faltantes al inicio
  }
  console.log(toCodePoint("a"));
  console.log("como codigo \u0061");

  ```

- librerias
  - npm install request
  - npm install request-promise
  - npm install node-fetch
  - ejemplos de generadoes y donde se usan
    - https://github.com/tj/co
    - https://github.com/redux-saga/redux-saga
