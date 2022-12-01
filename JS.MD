# ⚡ Marujeo del JavaScript ⚡

## Índice

 
  - [**Variables**](#variables)
  - [**Tipos de datos**](#tipos-de-datos)
  - [**typeOf**](#typeof)
  - [**Cambiar contenido HTML con getElementById()**](#cambiar-contenido-html-con-getelementbyid)
  - [**for**](#for)
  - [**while**](#while)
  - [**do while**](#do-while)
  - [**forEach**](#foreach)
  - [**for of**](#for-of)
  - [**for in**](#for-in)
  - [**break**](#break)
  - [**Arrays**](#array)
  - [**Objetos**](#objetos)
  - [**Operador Rest y Spread**](#operador-rest-y-spread)
  - [**Funciones**](#funciones)
  - [**Arrow Fuctions**](#arrow-functions)
  - [**Window**](#window)
  - [**Template literal**](#template-literal)
  - [**Convertir a STRING o NUMBER**](#convertir-a-string-o-number)
---




## **Variables**
---

Las variables son cajas, contenedores donde guardar datos y se pueden cambiar por otros. Es quiere decir que es **mutable**.
Básicamente hay de dos tipos: `let` y `const`. También existe `var`, que hay que evitar.

**var** → Declara una variable en el *scope* global. 🚨 Evitar su uso!

**let** → Variable que podrá se le podrá reasignar un valor. Es de *scope* local, dentro de una función por ejemplo.

**const** → Variable de solo lectura. No es posible cambiar su valor. Su *scope* es local como el *let*. Usaremos siempre `const` por defecto a menos que sepamos que su valor va ha cambiar, ahí usaremos `let`.

## **Tipos de datos**
---

String → Secuencia de caracteres que representan un valor.
Number → Valor numérico.
Boolean → True o False.
Null → Valor nulo. JS es *case-sensitive*. No es lo mismo Null, que NULL o null.
Undefined → Valor sin definir.
Symbol → Tipo de datos cuyos casos son únicos e inmutables.
Object → Objeto. Y puede contener más variables en su interior.
Nan → Not A Number

## **typeOf**
---
El operador `typeOf`devuelve el tipo de dato del operando.
La llamada a `typeOf x` devuelve una cadena con el nombre del tipo:
```
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "hola" // "string"

typeof Symbol("id") // "symbol"

typeof Math // "object"

typeof null // "object"

typeof alert // "function"

```
## **Cambiar contenido HTML con getElementById()**
---

getElementById() → El siguiente ejemplo "busca" un elemento HTML (con id="demo") y cambia el contenido del elemento (innerHTML) a "Hello JavaScript": 

`document.getElementById("demo").innerHTML = "Hello JavaScript";`

```
<p id="demo">JavaScript can change HTML content.</p>

<button type="button" onclick='document.getElementById("demo").innerHTML = "Hello JavaScript!"'>Click Me!</button>

```
![getElementById](./img/getElementById_01.png)

## **for**
---
Los *loops*, los necesitamos para crear un bucle tanta veces como queramos. Es habitual repetir acciones y de ahí los *loops*.

```
for (inicio; condición; incremento){
    // instrucción
}
```
**inicio** → És una variable declarada que hará de contador.

**condición** → El *loop* se ejecuta mientras la condición se cumple.Determinará el número de veces que se ejecuta.

**incremento** → Actualiza el valor incrementando o reduciendo el contador.

**intrucción** → Mientras la *condición* sea `true`, se ejecutará la *intrucción*.



```
for (let i = 0; i < 100; i++){
  console.log('hello world!')
}
```
```
let alumnos = ['Pepe', 'Paco', 'Ana', 'Luisa', 'Juan'];
let contenido = "Lista de alumnos:\n";

for (let index = 0; index < alumnos.length; index++) {
    contenido += `${index} ${alumnos[index]} \n`;
};

console.log(contenido);
/*
Lista de alumnos:
0  Pepe 
1  Paco 
2  Ana 
3  Luisa 
4  Juan 
*/
```

```
// Sumar los valores del 1 al 10
let suma = 0
for (let i = 1; i <= 10; i++) {
    suma += i
}
console.log(`La suma de los números del 1 al 10 es: ${suma}`) // 55
```

## **while**
---
Mientras la condición `condition` sea verdadera, el código del cuerpo del bucle será ejecutado.

```
while (condition) {
  // Código
  // Llamada "cuerpo del bucle"
}
```

Por ejemplo, el bucle siguiente imprime `i` mientras se cumpla `i < 3`:

```
let i = 0;
while (i < 3) { // Muestra 0, luego 1, luego 2
  alert( i );
  i++;
}
```

## **do while**
---
Similar a `while` solo que nos aseguramos que almenos de ejecute una vez.
```
do {
  // cuerpo del bucle
} while (condition);
```

```
let counter = 0

do {
    console.log('hello world!')
    counter++
} while (counter < 10) // Muestra 10 mensajes de "hello world!"
```
## **forEach**
----
`forEach` es un método de **array**, muy común, y sirve para recorrer un array sin escribir una estructura.
A menudo te verás con la necesidad de iterar a través de una colección de *arrays* y ejecutar un método *callback* por cada una de las iteraciones. Y para realizarlo hay un método muy útil: el método `forEach()`.

La función *callback* puede recibir tres parámetros.

- El elemento actual: Este es el elemento del arreglo por el cual se está haciendo la iteración.
- Su índice: Este es el índice de la posición que tiene el elemento dentro del array.
- El array objetivo: Este es el array por el cual se está haciendo la iteración.

🚨 Con `forEach` **NO** puedes terminar el bucle con la instrucción `break`.

```
let alumnos = ['Pep', 'Cesc', 'Anna', 'Lluisa', 'Joan'];
let content = "Listado de alumnos:\n";

alumnos.forEach(function(alumno, position) {
    content += `${position} ${alumno} \n`;
})

console.log(content);

/*
Listado de alumnos:
0  Pep 
1  Cesc 
2  Anna 
3  Lluisa 
4  Joan 
*/
```
```
let group = {
  title: "Our Group",
  students: ["John", "Pete", "Alice"],

  showList() {
    this.students.forEach(
      student => console.log(this.title + ': ' + student)
    );
  }
};

group.showList();

/* 
"Our Group: John"
"Our Group: Pete"
"Our Group: Alice"
*/
```

```
let numeros = [3, 6, 8, 10, 12]
let impar = 3;

numeros.forEach(function(numero) {
    if (numero === impar) {
        numeros.shift() // 3 será borrado del arreglo
    }
})

console.log(numeros);

[6, 8, 10, 12] // Todos son pares!
```
En el siguiente ejemplo, vamos a ejecutar la función  `pasarLista` por cada  uno de los estudiantes por los que se recorre el bucle dentro del array. La función `pasarLista` solamente registra en la consola un *string* perteneciente a cada uno de los estudiantes.
```
nombres = ["Anna", "Alicia", "Quim", "Guido", "Eva"]

function pasarLista(nombre, indice) {
    console.log(`Está el numero de estudiante ${indice + 1}  -${nombre} - presente? Sí!`)
    ;}

numeros.forEach((nombre, indice) => pasarLista(nombre, indice));


/*
"Está el número de estudiante 1  - Anna presente? Sí!"
"Está el número de estudiante 2  - Alicia presente? Sí!"
"Está el número de estudiante 3  - Quim presente? Sí!"
"Está el número de estudiante 4  - Guido presente? Sí!"
"Está el número de estudiante 5  - Eva presente? Sí!"
*/
```
## **for of**
----
`for...of` es otro método de iterar arrays. En este caso, no tenemos acceso al número de veces que hemos iterado, sólo al valor de cada elemento del array.
```
let fruits = ["Apple", "Orange", "Plum"];

for (let fruit of fruits) {
  console.log( fruit );
}

/*
"Apple"
"Orange"
"Plum"
*/

```
## **for in**
----
`For...in` es un método en este caso para iterar objetos. Creará una variable que será la key de cada propiedad del objeto.

```
let film = {title: 'El padrino', director: 'Francis Ford Coppola', year: 1972, score: 9}

for (let key in film) {
    console.log(`La key -> ${key} \nEl valor -> ${film[key]} `)
};

/*
La key -> title 
El valor -> El padrino 
La key -> director 
El valor -> Francis Ford Coppola 
La key -> year 
El valor -> 1972 
La key -> score 
El valor -> 9 
*/
```

## **break**
---
Normalmente, un loop continúa mientras la condición es truey se detendrá el bucle cuando la condición sea false.

Pero podemos forzar que se acabe el bucle utilizando la palabra `break`.

```
let sum = 0;

while (true) {

  let value = Number(prompt("Enter a number", ''));

  if (!value) break;

  sum += value;

}
console.log( 'Sum: ' + sum );
```
## **Arrays**
---
Estructura de datos que nos permite almacenar múltiples valores en una misma estructura. Parecido a una lista. Se separa con `,` (comas)

Chuleta JavaScript - Array [link](https://www.tutorialesprogramacionya.com/herramientas/chuletajs/chuletamasejemplo.html#array) ← *Click derecho - Abrir vínculo en una pestaña nueva.*
<https://www.tutorialesprogramacionya.com/herramientas/chuletajs/chuletamasejemplo.html#array>

```
const miArray = [ 'Laia', 4 ];
console.log(miArray); // [ 'Laia', 4 ]

const estudiantes = [ 'Pol', 'Anna', 'Joan', 'Èlia' ];
console.log(estudiantes); // [ 'Pol', 'Anna', 'Joan', 'Èlia' ]

const notas = [ 95, 67, 89, 56 ];
console.log(notas); // [ 95, 67, 89, 56 ]
```

### Array anidados

```
const unNombre = [[], []];
```
```
const listaEstudiantes = [['Daniel', 95],['Carmen', 97]];
console.log(listaEstudiantes) // [ [ 'Daniel', 95 ], [ 'Carmen', 97 ] ]
```
### Cambiar el valor de un Array

Para cambiar un valor dentro de una **array** se hace como si de una variable se tratára.

```
const miArray = [ 10, 20, 30 ];
miArray[1] = 'Hola'; // <- Le damos el valor 'Hola' a la posición 1, que de inicio tenía 20.

console.log(miArray); // [ 10, 'Hola', 30 ]
```
Y podemos anidar Arrays en una posición.

```
const miArray = [ 10, 20, 30 ];
miArray[1] = [1, 2, 3];

console.log(miArray); // [ 10, [ 1, 2, 3 ], 30 ]
```
### Acceso a Arrays multidimensionales (anidados)


## **Objetos**
---
## **Operador Rest y Spread**
---

El operador **Rest** disponible en (JS ES6) sirve para recibir cualquier número de parámetros en una función en forma array.

Si lo declaramos en los *argumetos* de vuelve un array.
```
function miFuncion(...args) { // args o cualquier otro nombre.
  console.log(args);
}

miFuncion(1, 2, 3, 4); // [1, 2, 3, 4]

```
O así:

```
const miFuncion = (...args) => console.log(args);


miFuncion(1, 2, 3, 4);  // [1, 2, 3, 4]

```
Si lo declaramos en la función, realiza acciones dentro del array. Y los descompone el array en sus elementos individuales y asignarlos en orden a los parámetros. Aplicado asó este operador se llama **Spread**
```
const numeros = [1, 2, 3];

const sumar = (x, y, z) => x + y + z;

// sumar(numeros[0],numeros[1],numeros[2] ); // <- Así sería la operación sin **rest**

console.log(sumar(...numeros)); // 6

```


## **Funciones**
---
`function` *nombreDeLaFuncion* seguido de `()`. Y entre las *curly braces* `{ }` pondremos las **instrucciones**.

```
function sayHi() {
  console.log('Hello!')
}

sayHi() // "Hello!"

```

### Devuelven valores: `return`
Una función puede devolver un valor al código de llamada como resultado.

El ejemplo más simple sería una función que suma dos valores:

```
function sum(a, b) {
  return a + b;
}

let result = sum(1, 2);
alert( result ); // 3
```
```
function checkAge(age) {
  if (age > 18) {
    return true;
  } else {
    return confirm('¿Tienes permiso de tus padres?');
  }
}

let age = prompt('¿Qué edad tienes?', 18);

if ( checkAge(age) ) {
  alert( 'Acceso otorgado' );
} else {
  alert( 'Acceso denegado' );
}
```


🚨 Todo el código después del `return`, no se ejecutará. El `return` pone fin a la acción de la función.
```
const value1 = 4
const value2 = 4

function average(){ 

   	let result
   	result = (value1 + value2) / 2 
   	return result
    result = 0 // <- Esta línea nunca se ejecutará.
}

const averageResult = average()
averageResult // 4
```
## **Arrow Functions**
---
Las *arrow functions* permiten simplificar las funciones mejorando su expresividad.

Hay varias formas de crear una *arrow function*. Por ejemplo, podemos crear una *arrow function* sin necesidad de poner `()` después del `=` siempre y cuando la función no necesite parámetros o solo tenga uno.
Entonces, la siguiente función:
```
function saludar (){
  const nombre = 'Quim';
  console.log('Hola');
}
saludar(); // "¡Hola Quim!"
```
Para crear una *arrow function*, primero quitamos la palabra `function` y como esta función únicamente tiene un parámetro, podemos obviar los `()` y colocar la constante `nombre` seguida del símbolo de la `a.f`, que es este, `=>`.

🚨 Si la `a.f` ocupa solo una línea, esta ya lleva implícito el `return`, por lo que no haría falta escribirlo. También podemos omitir las `{ }`.

```
const saludar = nombre => console.log(`¡Hola ${nombre}!`);

saludar('Quim') // "¡Hola Quim!"
```

```
const sumar = function (a,b){
  return a + b;  
}

console.log(sumar(5,5)); // 10
```
Y aquí tenemos lo mismo con una `arrow function`
La función tiene dos parámetros, y en este caso sí que debemos poner `()`, seguido de `=>` y la instrucción. Tampoco necesita `return` ni `{ }`.

```
const sumar = (a,b) => a + b;

console.log(sumar(5,5)); // 10
```
🚨 Con las funciones de flecha no hay vinculación de `this`. Haría referencia a `Window` 

Más ejemplos...

```
const concatenarArrays = function(arr1, arr2) {
  return arr1.concat(arr2);
};

console.log(concatenarArrays([1, 2], [3, 4, 5])); // [ 1, 2, 3, 4, 5 ]
```
Versión `a.f`
```
const concatenarArrays = (arr1, arr2) => arr1.concat(arr2);

console.log(concatenarArrays([1, 2], [3, 4, 5])); // [ 1, 2, 3, 4, 5 ]
```

Y cuando la función ocupa varias líneas funciona de la siguiente manera:
```
const sumar = function(a, b) {
  let num = 6;
  return a + b + num;
}

console.log(sumar(1,1)); // 8

```
En `a.f`.
```
const sumar = (a, b) => {
  let num = 6;
  return a + b + num;
}

console.log(sumar(1,1)); // 8
```
Tunear un valor por defecto es posible, *look at this* ⬇

```
const incrementar = (num, valor = 1) => num + valor;

console.log(incrementar(5, 3)); // <- Aquí le pasamos el valor 3, como nuevo valor (que era 1) y el resultado es 8
```
## **Window**
---
Podemos utilizar el **objeto especial** `Window` para acceder directamente al ámbito global del DOM independientemente de donde nos encontremos. Esto ocurre así porque las variables globales se almacenan dentro del objeto Window, es la ventana del navegador web.

```
let a = 1;
console.log(a); // Aquí accedemos a la "a" global, que vale 1

function x() {
  console.log(a); // En esta línea el valor de "a" es 1
  a = 5; // Aquí creamos una variable "a" en el ámbito anterior

  console.log(a); // Aquí el valor de "a" es 5 (a nivel de función)
  console.log(window.a); // Aquí el valor de "a" es 5 (ámbito global)
}

x(); // Aquí se ejecuta el código de la función x()
console.log(a); // En esta línea el valor de "a" es 5

```
## **Template literal**
---
Ejemplo:
```
let name = "Quim";
alert( `Hola, tu nombre es ${"name"}.`); // Hola, tu nombre es Quim.
```

## **Convertir a STRING o NUMBER**
---
Escribimos String, Number para covertir valores.

```
let value = true;
alert(typeof value); // boolean

value = String(value); // ahora value es el string "true"
alert(typeof value); // string
```

Nota:
Los string "afectados" por un operador lógico serán convertidos a números.
```
alert( "6" / "2" ); // 3, los strings son convertidos a números
```

##
