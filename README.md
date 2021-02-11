# ECMAScript6

---

El contenido de este repositorio es tener una guía del curso de ECMAScripts 6.

## ¿Que es EGMAScript?

---

ECMAScript es la especificación donde se mencionan todos los detalles de cómo debe funcionar y comportarse Javascript en un navegador. De esta forma, los diferentes navegadores (Chrome, Firefox, Opera, Edge, Safari…) saben como deben desarrollar los motores de Javascript para que cualquier código o programa funcione exactamente igual, independientemente del navegador que se utilice.

ECMAScript suele venir acompañado de un número que indica la versión o revisión de la que hablamos (algo similar a las versiones de un programa). En cada nueva versión de ECMAScript, se modifican detalles sobre Javascript y/o se añaden nuevas funcionalidades, manteniendo Javascript vivo y con novedades que lo hacen un lenguaje de programación moderno y cada vez mejor preparado para utilizar en el día a día.

## Default Params y Concatenación

La siguiente función muestra como se definía una función donde sus parámetros tienen un valor por defecto.

```
function newFunction(name, age, country) {
  var name = name || "oscar";
  var age = age || 32;
  var country = country || "EC";
  console.log(name, age, country);
}
```

Con EGMA 6 se puede definir dentro de la función los valores por defecto

```
function newFunction2(name = "oscar", age = 32, country = "Ec") {
  console.log(name, age, country);
}
```

La forma de llamar a dichas funciones es la misma

```
newFunction2();
newFunction2("Javier", 23, "CO");
```

**Resultado**

```
oscar 32 Ec
Javier 23 CO
```

La forma de concatenar strings:

```
let hello = "hello";
let world = "world";
```

Usando el signo **+**

```
let epicPhrase = hello + " " + world;
console.log(epicPhrase);
```

**Resultado**

```
hello world
```

En ECMAScrip 6 se tiene:

```
let epicPhrase2 = `${hello} ${world}`
console.log(epicPhrase2);
```

**Resultado**

```
hello world
```

## LET y CONST, Multilínea, Spread Operator y Desestructuración

Se puede hacer un salto de linea con **\n**

```
let lorem = "Quiero escribir una frase épica \n" + "Es otra frase épica";
```

En ECMAScript 6 se utilizan las comillas inglesas **`**

```
let lorem2 = `Nueva frase épica
ahora esta es otra frase épica`;
```

```
console.log(lorem);
console.log(lorem2);
```

**Resultado**

```
>> Quiero escribir una frase épica
Es otra frase épica

>> Nueva frase épica
ahora esta es otra frase épica
```

### Des estructuración de elementos

La forma antigua se lo realizaba asignando el valor para cada parámetro

```
let person = {
name: "Oscar",
age: 32,
country: "EC",
};

console.log(person.name);
console.log(person.age);
console.log(person.country);
```

Se puede obtener los valores asignando directamente a las variables

```
let { name, age, country } = person;

console.log(name, age, country);
```

Puedes unir de forma amigable diferentes elementos con ECMAScript 6

Se utiliza **...{Nombre del array}**

```
let team1 = ["Oscar", "Julian", "Ricardo"];
let team2 = ["Valeria", "Jessica", "Camila"];

let education = ["David", ...team1, ...team2];
console.log(education);
```

**Resultado**

```
>> Array(7)
0: "David"
1: "Oscar"
2: "Julian"
3: "Ricardo"
4: "Valeria"
5: "Jessica"
6: "Camila"
```

### Uso de Let

Let es para guardar elementos en memoria con let solo esta disponible en el scope, es decir dentro del bloque en donde se ha definido la variable.

```
{
var globalVar = "Global Var";
}

{
let globalLet = "Global Let";
console.log(globalLet); //Esta variable si se imprime
}

console.log(globalVar);
console.log(globalLet); //Se tiene error

```

**Resultado**

```
>> Global Let
>> Global Var
>> Uncaught ReferenceError: globalLet is not defined
    at <anonymous>:1:13
```

### Uso de **_const_**

Const es un avariable inmutable

```
const a = "b";
//No se puede asignar el valor
a = "a";
```

**Resultado**

```
>> Uncaught TypeError: Assignment to constant variable.
    at <anonymous>:1:2
```

En el siguiente gráfico describe el scope de **let var const**

![Scope](https://static.platzi.com/media/user_upload/const-vs-let-vs-var-f3270d36-0e39-4e0d-8ed1-2681991b84b2.jpg)

# Arrow Functions, Promesas y Parámetros en objetos

Las promesas permiten trabajar el asincronismo, y resuelven el callback hell que no es escalable.

La promesa requiere de una función donde sus parámetros son (resolve, reject)
**resolve** se ejecutará cuando la promesa es verdadera
**reject** se ejecutará cuando la promesa es falsa

```
const helloPromise = () => {
  return new Promise((resolve, reject) => {
    if (false) {
      resolve("hey!");
    } else {
      reject("ups!");
    }
  });
};


helloPromise()
  .then((response) => console.log(response))
  .catch((error) => console.log(error));
```

**then** Permite obtener el valor en verdadero
**catch** Se ejecuta cuando falla la promesa

## Clases, Módulos y Generadores

### Clases

Las Clases son una forma de manejar objetos y las herencias dentro de JS

```
class Calculadora {
  constructor() {
    this.valueA = 0;
    this.valueB = 0;
  }

  sum(valueA, valueB) {
    this.valueA = valueA;
    this.valueB = valueB;
    return this.valueA + this.valueB;
  }
}

const calc = new Calculadora();
console.log(calc.sum(3, 5));
```

### Import

También se trabaja ya con módulos con import.
Se usa el keyword **export default**

```
function helloModule() {
  return "Hello !";
}

export default helloModule;
```

```
import helloModule from "./module.js";
console.log(helloModule());
```

**Nota:** Si se tiene problemas con la ejecución ir al archivo **package.json** y agregar la palabra **"type": "module",**

```
{
  "type": "module",
  "name": "ecmascript",
  "version": "1.0.0",
  "description": "Entendiendo ecmascript",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/JaviDev27/ECMAScript6.git"
  },
  "author": "Javier Manobanda",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/JaviDev27/ECMAScript6/issues"
  },
  "homepage": "https://github.com/JaviDev27/ECMAScript6#readme"
}

```

<h3>Export default</h3>
Con export default podemos exportar una variable, o función por defecto de un archivo así:

```
function hello() {
	return'Hello!'
}

export default hello
```

Para importarla no necesitamos hacerlo con su nombre, podemos usar cualquier nombre y por defecto nos traerá la única variable o función que exportó así:

```
import myHello from'./module'
console.log(myHello())
```

<h3>Export nombrado</h3>
A diferencia del export default en esta ocasión podemos exportar más de una variable o función que se encuentre en nuestro archivo, pero para importarlas debemos hacerlo con el nombre exacto de esa variable entre llaves.

Para exportar lo hacemos así:

```
export function hello() {
return 'Hello!'
}

export const bye = 'Bye!'
```

Podemos importar solo lo que necesitemos así:

```
import { hello } from'./module'
console.log(hello())
```

También podemos importar más de un elemento nombrando cada uno

```

import { hello, bye } from'./module'

console.log(hello())
console.log(bye)

```

Podemos cambiarles los nombres

```

import { hello, bye as byeGreeting } from'./module'

console.log(hello())
console.log(byeGreeting)

```

Y podemos importar todas las funciones de una sola vez

```

import \* as allGreetings from'./module'

console.log(allGreetings.hello())
console.log(allGreetings.bye)

```

## Los Generator

Es una función especial que retorna una serie de valores según el algoritmo definido.

```

function\* helloWorld() {
if (true) {
yield "hello,";
}
if (true) {
yield "world";
}
}
const generatorHellow = helloWorld();

console.log(generatorHellow.next().value);
console.log(generatorHellow.next().value);
console.log(generatorHellow.next().value);

```

**Resultado**

```

> > hello,
> > world
> > undefined

```

Más información de los [generadores](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Generador)

## ¿Qué se implementó en ES7?

---

### Include

Include permite conocer si existe un elemento en un array
let numbers = [1, 2, 3, 4, 5, 6, 7];

```

if (numbers.includes(7)) {
console.log("Si se encuentra");
} else {
console.log("Si se encuentra");
}

```

## Función Exponente

En ES8 los se define con doble asterisco **\*\***

```

let base = 4;
let exponent = 3;
let result = base \*\* exponent;
console.log(result);

```

## ¿Qué se implementó en ES8?

---

### Object.entries

Devuelve la clave y los valores de una matriz.

```

const data = {
frontend: "oscar",
backend: "ISabel",
desing: "Ana",
};

const entries = Object.entries(data);
console.log(entries);

```

**Resultado**

```

[
[ 'frontend', 'oscar' ],
[ 'backend', 'ISabel' ],
[ 'desing', 'Ana' ]
]

```

### Length

Si queremos saber cuantos elementos tiene un objeto.

```

console.log(entries.length);

```

### Object.values

Obtiene solo los valores de un objeto

```

const data = {
frontend: "oscar",
backend: "ISabel",
desing: "Ana",
};

const values = Object.values(data);
console.log(values);

```

**Resultado**

```

> > [ 'oscar', 'ISabel', 'Ana' ]

```

### padStart y padEnd

padStart añade un string al inicio hasta completar el número de dígitos especificados.
Al contrario que padEnd añade un string al final hasta completar el número de dígitos especificados

```

const string = "hello";
console.log(string.padStart(8, "hi")); //Hasta completar 8 dígitos y coloca el string al inicio.
console.log(string.padEnd(12, "hi")); //Hasta completar 12 dígitos y coloca el string al inicio.
console.log("foot".padEnd(12, "---"));//Hasta completar 12 dígitos y coloca el string al final.

```

**Resultado**

```

> > hihhello
> > hellohihihih
> > foot--------

```

### TRAILING COMMA

Se aplica al último elemento, para evitar errores si a futuro quiero agregar mas elementos

```

const data = {
frontend: "oscar",
backend: "ISabel",
desing: "Ana", //Se agrega coma al final
};

```

### Async Await

Permite el manejo de asincronismos en JavaScript.

```

const helloWorld = () => {
return new Promise((resolve, reject) => {
if (true) {
setTimeout(() => {
resolve("helloWorld");
}, 3000);
} else {
reject(new Error("Test Error"));
}
});
};
const helloAsync = async () => {
const hello = await helloWorld();
console.log(hello);
};

helloAsync();

```

La forma correcta de ejecutar **async y await** es dentro de un **try-catch**

```

const anotherFunction = async () => {
try {
const hello = await helloWorld();
console.log(hello);
} catch (error) {
console.log(error);
}
};

anotherFunction();

```

## La version 9 es lanzada en Junio del 2018

### Operador de reposo

Puede extraer las propiedades de un objeto que no se ha contruido

```

const obj = {
name: "Javier",
age: 28,
country: "EC",
};

let { name, ...all } = obj;
console.log(name, all);

let { country, ...all2 } = obj;
console.log(all2);

```

Aqui sacas lo que necesitas.

**Resultado**

```

> > Javier { age: 28, country: 'EC' }
> > { name: 'Javier', age: 28 }

```

Se puede re escribir los parámetros de un objeto

```

const obj1 = {
...obj,
country: "CO",
};

console.log(obj1);

```

**Resultado**

```

> > { name: 'Javier', age: 28, country: 'CO' }

```

### Finaly

Se ejecuta al final de una promesa, si falla o no la promesa es indiferenete, este se ejecuta.

```

const helloWorld = () => {
return new Promise((resolve, reject) => {
true
? setTimeout(() => {
resolve("Hellow world");
}, 3000)
: reject(new Error("Test Error"));
});
};

helloWorld()
.then((response) => console.log(response))
.catch((error) => console.log(error))
.finally(() => console.log("finalizo")); //Este bloque se ejecuta al finalizar la promesa

```

### regexData

Permite hacer una expresion regular para separar partes de un string.

```

const regexData = /([0-9]{4})-([0-9]{2})-([0-9]{2})/;
const match = regexData.exec("2018-04-20");
const year = match[1];
const month = match[2];
const day = match[3];
console.log(year, month, day);

```

**Resultado**

```

> > 2018 04 20

```

## ¿Qué se implementó en ES10?

---

###Array.prototype.flat(nivel_de_profundidad)
La funcion flat va aplanando el arreglo según el nivel que se envie como parametro.
Array.prototype.flat(nivel_de_profundidad): un nuevo método que nos permite aplanar arreglos.

```

let array = [1, 2, 3, [1, 2, 3, [1, 2, 3]]];
console.log(array.flat());
console.log(array.flat(2));
console.log(array.flat(3));

```

**Resultado**

```

[ 1, 2, 3, 1, 2, 3, [ 1, 2, 3 ] ]
[
1, 2, 3, 1, 2,
3, 1, 2, 3
]
[
1, 2, 3, 1, 2,
3, 1, 2, 3
]

```

### Array.prototype.flatMap()

Array.prototype.flatMap() lo mismo que flat con el beneficio de que primero manipular la data para luego poder aplanar.

```

let array1 = [1, 2, 3, 4, 5];

console.log(array1.flatMap((value) => [value, value * 2]));

```

**Resultado**

```

[
1, 2, 2, 4, 3,
6, 4, 8, 5, 10
]

```

### String.prototype.trimStart() | String.prototype.trimEnd()

String.prototype.trimStart() | String.prototype.trimEnd() permite quitar los espacios al inicio o al final dependiendo de la funciona.

```

let hello2 = " hello world";
console.log(hello2);
console.log(hello2.trimStart());

```

**Resultado**

```

              hello world

hello world

```

```

let hello2 = "hello world ";
console.log(hello2);
console.log(hello2.trimEnd());

```

**Resultado**

```

hello world
hello world

```

### try/catch

try/catch: ahora puedes utilizarlo sin necesidad de especificaro como catch(error) sino directamente usarlo en el scope del catch.

```

try {
} catch {
error; //Ya tienes el valor
}

```

### Object.fromEntries()

Object.fromEntries() lo inverso a Object.entries(), es decir podemos convertir un objeto en una matriz clave/valor.

```

let entries = [
["name", "oscar"],
["age", "32"],
];

console.log(Object.fromEntries(entries));

```

**Resultado**

```

{ name: 'oscar', age: '32' }

```

### Symbol.prototype.description

Symbol.prototype.description: permite regresar la descripción opcional del Symbol.

```

let mySymbol = "My symbol";
let symbol = Symbol(mySymbol);
console.log(symbol.description);

```

**Resultado**

```

My symbol

```

Si quieres ams información del [Objeto Simbol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/description)

## ¿Qué es TC39?

El TC39 de Ecma International es un grupo de desarrolladores, implementadores, académicos y más de JavaScript, que colaboran con la comunidad para mantener y desarrollar la definición de JavaScript.

![Imgur](https://i.imgur.com/t80cJv2.png)

```

```
