# ⚡ Marujeo del JavaScript ⚡

## Índice

1. [Variables](#variables)
2. [Tipos de datos](#tipos-de-datos)
3. [typeOf](#typeof)
4. [Cambiar contenido HTML con getElementById()](#cambiar-contenido-html-con-getelementbyid)
5. [For](#for)
6. [Window](#window)
7. [Template Literal](#template-literal)
8. [Convertir a STRING o NUMBER](#convertir-a-string-o-number)
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

## **For**
---
Los Loops, los necesitamos para crear un bucle tanta veces como le indiquemos.

```
for (inicio; condición; incremento){
    // instrucción
}
```
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

## **Window**
---
Podemos utilizar el **objeto especial** window para acceder directamente al ámbito global independientemente de donde nos encontremos. Esto ocurre así porque las variables globales se almacenan dentro del objeto window (la pestaña actual del navegador web).

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

```
let name = "Quim";
alert( `Hola ${"name"}`); // Hola Quim
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



