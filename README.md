## Checkpoint 8

### 1) ¿Qué tipo de bucles hay en JS?
Los bucles ofrecen una forma rápida y sencilla de hacer algo repetidamente. Puedes pensar en un bucle como una versión computarizada del juego en la que le dices a alguien que dé _X_ pasos en una dirección y luego _Y_ pasos en otra.
Los diversos mecanismos de los bucles en Javascript ofrecen distintas formas de determinar los puntos de inicio y terminación del bucle. Dependiendo de las situaciones, serán atendidas por un tipo de bucle o por otros.

Para abarcar los tipos de bucles, vamos a hacer dos grandes bloques, los **bucles básicos** y los **bucles de objetos**.

#### BUCLES BÁSICOS:

#### a) El bucle "for"
- Se utiliza para repetir una serie de sentencias internas, tantas veces como bucles se determinen. El número de veces que se repite está prefijado, controlando sus límites de cuándo comienza y cuándo finaliza.
- Su diagrama de flujo es el siguiente: ![Diagrama de Flujo de un bucle For](https://www2.eii.uva.es/fund_inf/cpp/_images/for.jpg)
- La sintaxis de la declaración del bucle `for`tiene el siguiente aspecto:
	```
	for ([expresiónInicial]; [expresiónCondicional]; [expresiónDeActualización]) {
	  // Sentencias internas
	}
	```
- En la **expresión inicial** se declara una variable iteradora para determinar el punto inicial del bucle. 
	Por ejemplo: _let i = 1;_ _let i = 0;_ _let i = -30_ , _etc._
- En la **expresión condional** se impone un criterio que es necesario cumplir para dar acceso a las sentencias internas.
	Por ejemplo: _i < 10; i => array.length, etc._
	-> Si i = 10, ya no se cumple la condición, y se termina el bucle. 
- En la **expresión de actualización**, se hace avanzar la variable iteradora al siguiente bucle (puede avanzar en sentido positivo o negativo).
	Por ejemplo: _i++, i- -, i = i + 2, etc_
	Es la amplitud y el sentido de cada iteración del bucle. 

- Un ejemplo:
	```javascript
	for (var i = 0; i < 5; i++) {
	   console.log(i);
	};

	Resultado:
	0
	1
	2
	3
	4
	```
Explicación: 
i comienza en la posición "0", cumple con la condición, y se actualiza sumando un valor más en positivo. En cada paso, imprime el valor de i.  Y como se aprecia, cuando _i = 5_ no se  cumple la condición y por tanto, no inicia el código interno del bucle. Es por tanto el final del bucle. 

#### b) El bucle "while"
- El bucle while no tiene un número de repeticiones definido. Se seguirá repitiendo indefinidamente hasta que la condición inicial deje de cumplirse. 
- Su diagrama de flujo realiza el siguiente esquema:
![Diagrama de Flujo de un bucle While](https://www2.eii.uva.es/fund_inf/cpp/_images/while.jpg)
- Su sintaxis guarda la siguiente estructura:
```javascript
while  (condition)  {  
	// Sentencias internas o "cuerpo del bucle"  
}
```
- Entre paréntesis se escribe la **condición** que debe resultar _**True**_ para que se ejecuten las sentencias internas. Si resultan _**False**_, no se ejecuta el cuerpo del bucle y se cierra, continuando el flujo hacia abajo.
-  Un ejemplo:
	```javascript
	let i = 0; 
	while (i < 3){ 
		console.log(i); 
		i++;
	};

	Resultado:
	0
	1
	2
	```
Explicación: 
Comienza la variable _**i**_ con un valor _cero_, por tanto se cumple la condición `(i < 3)`, se imprimirá con la sentencia `console.log`, para después aumentar el valor de _i_ en 1. En el siguiente bucle, `ì = 1`, por tanto, cumple de nuevo, se imprime y aumenta el valor de _i_. 
Así entra en un nuevo bucle que imprimirá un 2, hasta que _i_ incrementa en 3, momento en que la condición ya no se cumple, resulta _False_ y no se ejecutan las sentencias internas, saliendo del bucle. 

NOTA IMPORTANTE: Mucho cuidado con codificar bucles infinitos, pues haría que el programa nunca se termine de ejecutar. **En algún momento, la condición debe resultar _False_**.

#### c) El bucle do...while
- El bucle do...while es muy similar al bucle while, porque determina un número indeterminado de bucles hasta que la condición establecida sea falsa. Sin embargo su estructura hace que al menos las sentencias internas o cuerpo del bucle, se ejecuten una vez.
- Su diagrama de flujo sería el siguiente:
![Diagrama de Flujo de un bucle Do...While](https://www2.eii.uva.es/fund_inf/cpp/_images/do_while.jpg)
- Su sintaxis guarda la siguiente estructura:
	```javascript
	do {
		// cuerpo del bucle
	} while (condition);
	```
- Como se puede apreciar, el flujo del programa entra antes en las sentencias del cuerpo del bucle que en la condición necesaria a cumplir. Por ello, siempre ejecuta su cuerpo una primera vez y a partir de ahí en cada bucle, se comprueba si la condición sigue resultando _True_.
- Un ejemplo:
	```javascript
	let ​​i = 0; 
	do { 
		console.log(i);
		i++; 
	} while (i < 3);

	Resultado:
	0
	1
	2
	```
Explicación: 
El flujo del programa entra en el cuerpo del bucle con `i = 0`, se imprime 0 y aumenta su valor a `i = 1`. Se evalúa la condición en `(i < 3)`, resulta _True_, y vuelve a entrar en un nuevo bucle. 
En el nuevo nuevo bucle, se imprime 1 y vuelve a aumentar a 2. Como aún cumple la condición, entra en el siguiente bucle. 
En el último bucle, imprime el valor 2, aumenta a 3, pero no cumple en este momento la condición, momento en el cual, sale del bucle. 

#### Etiquetas break/continue
Estas etiquetas nos sirven para controlar el flujo de bucles de un programa. 
- **Break** a grandes rasgos, nos permite salir en un punto determinado del bucle saltándose los pasos inferiores del resto del cuerpo del bucle. Por ejemplo:
```javascript
	let i = 0; 
	while (i < 5){
		if (i % 3 === 0) { 
			console.log("Es múltiplo de 3"); 
			break; // Hace terminar el bucle
		} 
		console.log(i); 
		i++;
	};
Resultado:
0
1
2
Es múltiplo de 3
(No se imprime el número 3 por sí sólo)
```
En el ejemplo vemos que cuando `i = 3`es múltiplo de 3, cumple la condición del condicional y entra el flujo del programa en el cuerpo del condicional. Imprime "Es múltiplo de 3", y con break, sale del bucle sin imprimirse el `console.log(i)` del final del interior del bucle.

- **continue** sin embargo, hace que salte el flujo del bucle en el que se encuentra y pase al siguiente bucle. Por ejemplo:
```javascript
	let i = 0; 
	while (i < 5){
		if (i % 3 === 0) { 
			continue; // Hace saltar al siguiente bucle
		} 
		console.log(i); 
		i++;
	};
Resultado:
0
1
2
4
```
Podemos comprobar que en el caso de de el valor de _i_ sea múltiplo de 3, salta el bucle al siguiente y no llega a imprimirse con `console.log`.

#### BUCLES DE OBJETOS:
Además de estos bucles básicos, JavaScript también dispone de unos bucles especializados para iterar sobre elementos de arrays y objetos:

#### d) Bucle for...in
- Se usa para iterar sobre las **propiedades** (nombres y valores) de los objetos en general.
- La sintaxis general sería:
```javascript
for (key in object) {
	// Se ejecuta el cuerpo para cada clave entre las 		propiedades del objeto
}
```
En cada vuelta de bucle, se asigna una propiedad a una nueva variable `key`, que tomará inicialmente la clave de la misma. Con ella también podemos obtener los valores que están asociados en cada una de las iteraciones.
- Veamos un ejemplo:
```javascript
let user = {
	name:"John",
	age: 30,
	isAdmin: true
};
for (let key in user) {
	// claves
	console.log( key ); // name, age, isAdmin
	// valores de las claves
	console.log(user[key]); // John, 30, true
}
```
Podemos observar que con el bucle for..in podemos iterar en un bucle de número determinado por cada pareja de clave-valor.

#### e) Bucle for...of
- Este tipo de bucle puede operar sobre cualquier tipo de objeto iterable como arrays, strings, colecciones DOM (NodeList), maps, sets, etc. 
- La sintaxis general es muy similar a la anterior:
```javascript
for (key of object) {
	// Cuerpo del bucle
}
```
En cada iteración, `key`toma el valor de cada uno de los elementos del objeto iterable.

- Veamos un ejemplo:
```javascript
const frutas = ['manzanas', 'naranjas', 'uvas'];

for (let element of frutas) {
  console.log(element);
}

// Resultado: manzanas, naranjas, uvas
```
Como se puede comprobar, no toma los índices del array, sino que sólamente opera sobre los valores de dichas iteraciones.

*Fuentes utilizadas:*
[MDN Web Docs](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Loops_and_iteration#declaraci%C3%B3n_for...in)
[JavaScript.info](https://es.javascript.info/while-for)
[UVA Escuela de Ingenierías Industriales](https://www2.eii.uva.es/fund_inf/cpp/temas/6_control_flujo_iterativo/for.html)

### 2) ¿Cuáles son las diferencias entre const, let y var?
Aunque para declarar una variable no sea necesario ninguna palabra previa al nombre de la variable, se recomienda para evitar errores, utilizar estas tres palabras claves: const, let y var.
Se utilizan por tanto, a la hora de declarar una variable, pero no podemos confundirlo tampoco con una tipificación de variables. En lugar de asignar un tipo de dato a la variable, lo que asignamos son dos cosas básicamente: 
	- El **alcance** o **scope** de la variable para ser utilizada.
	- Y la posibilidad de **reasignar** valores a dichas variables. 
	
Para poder comprender bien sus diferencias, vamos a comentar unos conceptos previos:

- **Alcance o "Scope"**: Puede definirse como  **el alcance que una variable tendrá en el código**. En otras palabras, el scope de las variables decide **a qué variables se tiene acceso en cada parte del código.** 
Dependiendo de dónde sean declaradas las variables, existen tres tipos de scope o alcance: el  **scope global** fuera de toda función o bloque, el  **scope local**, dentro de una función,  y el **scope de bloque**, que puede darse en un bloque if o for por ejemplo. 
Determinando dos tipos de variables, las de **alcance global** o las de **alcance local o de bloque**.
En un ejemplo de **variable local** o de alcance o ámbito local, si es declarada dentro de un bloque o una función, dará un error si la queremos utilizar fuera de ese bloque, que dirá que la variable no está definida. Por ejemplo:
```Javascript
function alumno() { 
	const soyEstudiante = true;
	console.log(soyEstudiante); 
} 
alumno(); // true  
console.log(soyEstudiante); // soyEstudiante is not defined
```
En el caso de **variable global** o de alcance global, serán siempre declaradas fuera de una función o de un bloque. Será posible acceder a este tipo de variables desde cualquier parte del código, ya sea dentro o fuera de una función. Por ejemplo:
```javascript
const soyEstudiante = true; 
function alumno() { 
	console.log(soyEstudiante); 
} 
alumno(); //true  
console.log(soyEstudiante); //true
```
**Diferencias entre let, const y var**
Cuando declaramos una variable **_let_  o  _const_** dentro de un bloque, **el alcance o scope que tendrá será sólo dentro de ese bloque**. 
Veamos este ejemplo para entenderlo mejor:
```javascript
let ejemplo = 'Esto está fuera del bloque'; 
if (true) { 
	let ejemplo = 'Esto está dentro del bloque';
	console.log(ejemplo); //Esto está dentro del bloque } 
console.log(ejemplo) //Esto está fuera del bloque
```
Como podemos ver, podemos declarar dos variables con el mismo nombre y no colapsaron, porque cada una de ellas está declarada dentro de un bloque distinto y sólo es posible acceder a su valor dentro de éste. 
Por otro lado, si ambas variables estuvieran declaradas dentro del mismo scope, un mensaje de error sería mostrado en nuestra consola.
```javascript
let ejemplo = 'Esto está afuera del bloque'; 
if (true) { 
	... } 
let ejemplo = 'Misma variable declarada dos veces'; 
// Error, ejemplo has already been declared
```
Sin embargo, cuando declaramos una variable con **_var_**, con la salvedad de declararlo entre llaves dentro de una función, **aunque se declare dentro de un bloque como if o for, se pueden  comportar como variables globales**, pudiendo actuar en cualquier punto del código, por tanto, puede ser más susceptible de provocar bugs. 
Ello es debido al **hoisting**, al que ya aludimos en otro Checkpoint anterior cuando hablamos de las funciones, que hace referencia al comportamiento de la ejecución de Javascript del código, que "eleva" las declaraciones de var y de funciones, y luego las inicializa. De este modo, el ámbito de una variable var se hace global. Con este gráfico tendremos una visión más general:
![Hoisting en Javascript](https://res.cloudinary.com/practicaldev/image/fetch/s--QzCv1bXR--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/kaf11wh85tkhfv1338b4.png)
En el ejemplo anterior, si cambiamos las variables declaradas con  _let_  por variables declaradas con  _var_, nos resulta:
```javascript
var ejemplo = 'Esto está fuera del bloque'; 
if (true) { 
	var ejemplo = 'Esto está dentro del bloque';
	console.log(ejemplo); //Esto está dentro del bloque } 
console.log(ejemplo) //Esto está dentro del bloque
```
- La **reasignación**: es la última característica a tener en cuenta para entender bien el uso de las diferencias entre let, const y var. 
Lo primero a tener en cuenta es que redeclaración y reasignación no son lo mismo. Redeclaración es volver a declarar la misma variable con otro valor, y ello sí que lo permite la variable var, pero no es posible con let o const. 
```javascript
var x = 1;
var x = 2;
// No da ningún tipo de error
```
Sin embargo, la reasignación es posible en var y en let, son sin embargo con const.
```javascript
var x = 1;
x = 2;
// No da ningún tipo de error
let y = 1;
y = 2;
// No da ningún tipo de error
const z = 1;
z = 2;
// TypeError: invalid assignment to const
```
Por tanto, la variable const permite declarar e inicializar sólo una vez una variable, y la guarda como **valores inmutables** en el caso de valores primitivos (number, strings, booleans..) o como **referencias mutables** en el caso de arrays u objetos, porque ellos en sus valores internos que almacenan, sí pueden cambiar, pero la referencia no. 

Como recomendación final, normalmente si queremos que un valor no se cambie, utilizaremos variables **const** y si vamos a requerir que cambien, utilizaremos variables **let**. Las variables  **var** pocas veces son recomendables porque pueden originar bugs fácilmente, sobre todo si el código es muy extenso.

*Fuentes utilizadas:*
[FreeCodeCamp](https://www.freecodecamp.org/espanol/news/var-let-y-const-cual-es-la-diferencia/)
[MDN Web Docs](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/let)
[Platzi](https://platzi.com/blog/la-diferencia-entre-let-y-var/)
[Patrick's blog](https://writesbypatrick.hashnode.dev/redeclaring-variables-in-javascript)

### 3) ¿Qué es una función de flecha?
Una función flecha o _arrow functions_ es una alternativa más compacta a una expresión de función. Sin embargo su uso es limitado, y no sustituirán la estructura tradicional de una función.
Algunas de esas diferencias y limitaciones se pueden encontrar en la documentación de [MDN Web Docs](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Functions/Arrow_functions).
Fue una de las características más populares de la actualización de Javascript en ES6 (EcmaScript 6) en 2015, y se explicó con ella distintas sintaxis posibles para escribir una función de manera más simplificada. 
Empecemos observando, paso a paso, la descomposición de una "función tradicional" hasta la "función flecha" más simple:  
**Nota**: Cada paso a lo largo del camino es una "función flecha" válida
```javascript
// Función tradicional
function (a){
  return a + 100;
}

// Desglose de la función flecha

// 1. Elimina la palabra "function" y coloca la flecha entre el argumento y el corchete de apertura.
(a) => {
  return a + 100;
}

// 2. Quita los corchetes del cuerpo y la palabra "return" — el return está implícito.
(a) => a + 100;

// 3. Suprime los paréntesis de los argumentos
a => a + 100;
```
**Nota:** Como se muestra arriba, los { corchetes }, ( paréntesis ) y "return" son opcionales, pero pueden ser obligatorios.

Ahora vamos a ver una a una las variantes de las funciones flecha más utilizadas:

#### 1) Función de un solo parámetro.
Al crear una arrow function de un solo parámetro no es necesario escribír los paréntesis, tampoco es necesario escribír las llaves. Ello se puede hacer cuando la función es de una sola línea y devuelve un solo valor. Ejemplo:
```javascript
let saludo = nombre => `Hola ${nombre}`;

console.log(saludo('Jonathan'));  
//Imprime: Hola Jonathan
```
#### 2) Función de varios parámetros
Cuando la función tenga más de un parámetro es necesario envolver el nombre de ellos entre paréntesis.
```javascript
let sumar = (a, b) => a + b;

console.log(sumar(10, 9));  
//Imprime: 19
```
#### 3) Función sin parámetros
Cuando la función no reciba parámetros también necesita paréntesis. Ejemplo:
```javascript
let saludo = () => `Hola a tod@s`;

console.log(saludo());  
//Imprime: Hola a tod@s
```

#### 4) Función con cuerpo
Cuando la función tiene más de una línea (o no devuelve ningún valor) es necesario utilizar las llaves.
```javascript
let fecha = new Date(), hora = fecha.getHours(); 
let saludo = (hr) => {  
	if (hr <= 5) { 
		return 'Qué me dices!!!';
	} else  if(hr >= 6 && hr <= 11) {
		return  'Buenos días!!!';
	} else  if(hr >= 12 && hr <= 18) {
		return  'Buenas tardes!!!';
	} else {
		return  'Buenas noches!!!';
	} 
};

console.log(saludo(hora));
//Imprime el saludo dependiendo la hora del día
```

#### 5) Sintaxis avanzada
También admite sintaxis más concretas para casos especiales:
_**a) Para `objetos literales`**_
Para devolver una expresión de objeto literal, se requieren paréntesis alrededor de la expresión:
```javascript
(params) => ({ foo: "a" }); 
// devuelve el objeto {foo: "a"}
```
_**b) Los  `parámetros rest`  son compatibles**_
```javascript
(a, b, ...r) => expression;
```
_**c) Se admiten los  `parámetros predeterminados`**_
```javascript
(a = 400, b = 20, c) => expression;
```
_**d) `Desestructuración`  dentro de los parámetros admitidos**_
```javascript
([a, b] = [10, 20]) => a + b; 
// el resultado es 30
({ a, b } = { a: 10, b: 20 }) => a + b; 
// el resultado es 30
```

#### ¿Cuándo usar una función flecha y cúando no?
#### _a) No se recomiendan para el uso de métodos en objetos:_
Para entender mejor esta circunstancia, empezaremos hablando del correcto uso de `this`en una función flecha.
En una función regular,  `this` se define por cómo se llama la función. En cambio, las funciones flecha **heredan el valor de `this` del contexto donde se las define**, no de dónde se las invoca.

Veamos un ejemplo:
```javascript
const persona = {
  nombre: "Juan",
  saludar: function() {
    console.log("Hola, mi nombre es", this.nombre);
  }
}

persona.saludar(); // "Hola, mi nombre es Juan"

const saludarFlecha = () => {
  console.log("Hola, mi nombre es", this.nombre);
}

persona.saludarFlecha(); // Error!
```
En el primer caso,  `this.nombre` dentro de la función `saludar` se refiere a `"Juan"` porque la función se llama como un método del objeto `persona`.

En el segundo caso, la función flecha `saludarFlecha` no hereda el `this` de `persona` porque se define dentro del objeto. Entonces,  `this.nombre` dentro de la función flecha no apunta a nada y generará un error.

Y por la misma causa, no es recomendable usar la función flecha para definir métodos. Como por ejemplo en este caso:
```javascript
const coche = { 
	velocidad: 0, 
	acelerarFlecha: () => { 
		this.velocidad += 10; } 
}; 
coche.acelerarFlecha(); 
console.log(coche.velocidad); // Imprime NaN 
``` 
Porque `this` no tiene contexto en la función flecha y tampoco está dentro de otra función padre para que así lo tenga.

#### _b) No pueden usarse para crear constructores_
Las funciones flecha tampoco se recomiendan como constructores porque no tienen su propio objeto `prototype` . Al crear objetos con `new`, la función debe proporcionar un objeto prototype para que las nuevas instancias hereden las propiedades y métodos. Las funciones regulares sí poseen esa propiedad heredable, pero la función flecha no pueden hacer esto de manera confiable. Por ejemplo:
```javascript
var Foo = () => {};
var foo = new Foo(); // TypeError: Foo no es un constructor
```
#### _c) Funciones que utilizan el objeto `arguments`_
`Arguments` es un objeto similar a un array que se usa en funciones que reciben un numero variable de argumentos. Sin embargo, debido a que las funciones flecha no tienen su propio objeto `arguments`, se recomienda evitar usar funciones que no sean las regulares para esta funcionalidad. Ejemplo:
```javascript
function sumar() { 
	// Accedemos a los argumentos pasados a la función
	const argumentos = arguments; 
	let total = 0; 
	// Recorremos los argumentos y los sumamos 
	for (let i = 0; i < argumentos.length; i++) { 
		total += argumentos[i]; } return total; 
	} 
	// Llamamos a la función con varios argumentos 
	const resultado = sumar(5, 7, 3, 2); 
	console.log(resultado); // imprime 17
```
NOTA FINAL: 
Es importante tener en cuenta que las funciones flecha anónimas conllevan que puedan originarse algunos problemas:
1.  Más difíciles de depurar:
Si se obtiene un error, es difícil rastrear el nombre de la función o el número de línea exacto donde ocurrió.
2. Sin autorreferencia:
Si la función necesita tener autorreferencia en algún punto (por ejemplo, recursión, controlador de evento que necesita desvincularse), no funcionará.

_Fuentes utilizadas:_  
[MDN Web Docs](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
[FreeCodeCamp](https://www.freecodecamp.org/espanol/news/cuando-y-por-que-debes-usar-las-funciones-flecha-de-es6-y-cuando-no/)
[Ed Team](https://ed.team/blog/arrow-functions-en-javascript)
[Javascript.info](https://es.javascript.info/constructor-new)

