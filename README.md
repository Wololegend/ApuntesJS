# Apuntes JavaScript

[Tutorial original](https://www.youtube.com/watch?v=PkZNo7MFNFg)

## Tipos de variables

Las variables en JS pueden ser de cualquier tipo y cambiarse durante la ejecución del programa.

```js
var X = "Esto es un string";

...

X = 8;
```

* **var**: Tipo de variable global. Se puede utilizar durante toda la ejecución del código y se pueden declarar varias con el mismo nombre.

* **let**: Tipo de variable local. Sólo se puede utilizar en el segmento en el que fue declarada y no se pueden declarar varias con el mismo nombre.

* **const**: Constante. No se puede cambiar su valor.

## Mostrar valores por consola

Lo siguiente muestra _Hello World_ por pantalla.

```js
console.log("Hello World")
```

## Strings

Las cadenas de caracteres se pueden concatenar cómodamente de las siguientes formas:

```js
var string = "Hola" + "Mundo";

    console.log(string); //Hola Mundo

string += ", ¿Qué tal?";

    console.log(string); //Hola Mundo, ¿Qué tal?

var a = "Mundo";
var b = "Hola" + a

    console.log(b); //Hola Mundo
```

Para obtener el largo de un string utilizamos el método _length()_.

Para acceder a una posición utilizamos corchetes (_string[0]_).

En JS los strings son inmutables. Es decir, no podemos cambiar sus caracteres individualmente, sino todo el string.

```js
var string = "Wola mundo";

string[0] = "H"; //ERROR

string = "Hola mundo"; //CORRECTO
```

## Arrays
Los arrays en JS pueden mezclar tipos de datos en un sólo vector.

``` js
var array = ["Pepe", 2.75, true, ["E1", "E2"]];

    console.log(array[1]); //2.75
    console.log(array[3][0]); //E1
```

También hay ciertas funcionalidades de los vectores que son interesantes:

```js
var array = [1, 2, 3];

// Push añade un elemento al final del array
array.push(4);

    console.log(array[3]); //4

//Pop elimina el último elemento del array
array.pop();

    console.log(array); //[1, 2, 3]

//Shift elimina el primer elemento del array
array.shift();

    console.log(array); //[2, 3]

//Unshift añade un elemento al principio del array
array.unshift(1);

    console.log(array[0]); //1
```

## Clases

Las clases en JS se declaran de la siguiente forma:

```js
var clase = {
    "atributo1": 1,

    "atributo2": 2.75,

    "atributo3 vector": ["E1", "E2"]
};

console.log(clase.atributo1) //1

console.log(clase["atributo3 vector"][0]); //E1

//Podemos añadir y eliminar atributos a las clases

clase.atributo4 = true;
delete clase.atributo4;

//También podemos comprbar la existencia de un atributo

clase.hasOwnProperty(atributo1); //true
clase.hasOwnProperty(atributo4); //false
```

También podemos anidar objetos en arrays:

```js
var myMusic = [
    {
        "artist": "Billy Joel",

        "title": "Piano man"
    },

    {
        "artist": "ACDC",

        "title": "Highway to Hell"
    }
];

console.log(myMusic[0].artist); //Billy Joel
```

## Generar números aleatorios

   * **Decimales**: `Math.random();`

   * **Enteros**: `Math.floor(Math.random() * 20);` Generamos un número entre 0 y 19.

Generar números aleatorios en un rango concreto:

```js
var min = 5;
var max = 15;

var random = Math.floor(Math.random() * (max - min + 1)) + min;
```

## ParseInt

Es una función que permite convertir cadenas en enteros:

```js
var int = 7 + parseInt("3");

console.log(int); //10
```

También permite convertir cómodamente números en diferentes bases a decimal:

```js
var int = 7 + parseInt("11", 2); //(número, base)

console.log(int); //10
```

## Mutación de datos

En teoría, si declaramos una variable como const sólo se puede leer, no editar. Pero no es el caso con los arrays y las clases:

```js
const ARRAY = [1, 2, 3];

ARRAY = [3, 2, 1]; //ERROR

ARRAY[0] = 3;
ARRAY[2] = 1; //CORRECTO

//Para prevenir la mutación

Object.freeze(ARRAY);

ARRAY[0] = 1; //ERROR
```

## Funciones anónimas

Por antiintuitivo que parezca, en ocasiones se utilizan funciones de un solo uso. Y si las vamos a utilizar una sola vez, ¿Por qué ponerle un nombre?

```js
//setTimeout(a, b): tras una espera de b milisegundos se ejecuta a.

setTimeout(function  () {
    console.log("Has esperado 1 segundo")
}, 1000);
```

## Arrow functions

Son funciones simplificadas. Se suelen utilizar para simplificar las llamadas a funciones que empleen funciones como parámetros:

```js
//Función normal

function sum(a, b) {
    return a + b;
}

console.log(sum(2, 2)); //4

//Arrow function

var sum = (a, b) => a + b;

console.log(sum(2, 2)); //4

//Arrow function y función anónima. Reducimos líneas de código.

console.log(function (a, b) => a + b);
```

## Rest operator

Sirve para indicarle a una función que se le va a pasar un número indefinido de argumentos. Este operador los mete en un array de nuestra elección y se señaliza con puntos suspensivos (...):

```js
const sum = (funvtion() {
    return function sum(...array) {
        return array.reduce((a, b) => a + b); // reduce opera con los valores de un array 
    };                                        // de la forma que le indiquemos
})();

console.log(sum(1, 2, 3, 4, 5)); //15
```

## Spread operator

Separa los elementos de un array en elementos individuales.

```js
// Si igualamos un array a otro, simplemente
// los dos apuntan a la misma dirección de memoria.

const array1 = ["A", "B", "C"];

var array2 = array1;

array1[0] = "Z";

console.log(array2); //["Z", "B", "C"]

// Pero si utilizamos el Spread Operator

array1[0] = "A";

array2 = [...array1]; // array2 es un vector cuyos elementos son los de array1

console.log(array2); //["A", "B", "C"]
```

## Destructuring operator

Similar al Spread operator pero para clases:

```js
const clase = {x: 1, y: 2, z: 3};

// Forma antigua de hacerlo
var a = clase.x;
var b = clase.y;
var c = clase.z;

// Utilizando Destructuring operator

var {x: a, y: b, z: c} = clase;
```

En clases anidadas funciona así:

```js
const clase = {
    c1: {x: 1, y: 2},
    c2: {x:3, y: 4}
};

var {c1: {x: a}} = clase;

console.log(a); //1
```

## Destructuración en vectores

Podemos destructurar un vector de forma cómoda así:

```js
const [a, b, , d, ,f] = [1, 2, 3, 4, 5, 6];

console.log(a, b, d, f); //1, 2, 4, 6
```

Podemos observar que cada variable se asigna a un elemento del array según su posición.

También se puede utilizar para intercambiar los valores de variables:

```js
var a = 1;
var b = 2;

[a, b] = [b, a];

console.log(a, b); //2, 1
```

## Destructuración y Rest operator

Podemos utilizar estos dos conceptos para, por ejemplo, eliminar los dos primeros elementos de un array:

```js
const array1 = [1, 2, 3, 4, 5];

function removeFirstTwo(genericArray) {
    const [a, b, ...array2] = genericArray;

    console.log("Deleted ", a); //Deleted 1
    console.log("Deleted ", b); //Deleted 2

    return array2;
}

const array3 = removeFirstTwo(array1);
console.log(array3); //[3, 4, 5]
```

## Utilizar destructuración para pasar parámetros a funciones

En este caso, vamos a destructurar una clase para pasarle sólo los atributos que queremos a una función:

```js
const clase = {
    a: 1,
    b: 2,
    c: 3
 // ...
    z: 27
};

const printAandB = ({a, b}) => console.log(a, b));

// Le pasamos toda la clase como parámetro, pero realmente sólo
// le estamos pasando los atributos a y b de esa clase.

printAandB(clase); //1, 2
```

