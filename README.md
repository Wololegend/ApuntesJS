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

Son funciones simplificadas que se llaman mediante una variable. Se suelen utilizar para simplificar las llamadas a funciones que empleen funciones como parámetros:

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