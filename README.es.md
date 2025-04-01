# Algoritmos y Notación Big O en Español

Autor original: Pavan Katepalli

Editado por:
- [Nick Bartlett](https://github.com/tteltrab)
- [Nick West](https://github.com/njwest)


## ¿Qué son los algoritmos?

Los algoritmos son básicamente funciones.

Las funciones son algoritmos si:

1. reciben argumentos

2. retornan valores explícitamente

#### 1.1 Ejemplo de un algoritmo

Algoritmo que cuenta el número de vocales en una palabra y devuelve el conteo:

```js
function countVowels(word) {
    var vowels = ['a', 'i', 'e', 'o', 'u'];
    var count = 0;
		for (var i = 0; i < word.length; i++) {
        for (var j = 0; j < vowels.length; j++) {
            if (word[i] === vowels[j]) {
                count++;
            }
        }
    }
    return count;
}

```

## ¿Cuándo las funciones no son algoritmos?
Cuando escribes una función, esta puede o no:

* tener argumentos

* retornar un valor

Las funciones que no reciben argumentos o no retornan un valor generalmente se utilizan para simplificar código repetitivo, mostrar algo en pantalla o servir como argumento para ser ejecutado más tarde. Estos tipos de funciones normalmente no se consideran algoritmos.

#### 1.2 Ejemplo de una función que no es un algoritmo

Una función anónima que se pasa a la función `on` de jQuery.

```js
$('button').on('click', function(){ 
	alert('hi') 
});
```

#### 1.3 Ejemplo de una función que no es un algoritmo

Esta función no tiene argumentos ni retorno

```js
function clearDiv(){
	$('#div').html("");
}
```
#### 1.4 Ejemplo de una función que no es un algoritmo

Esta función tiene un argumento, pero no retorno

```js
function clearDiv(text){
	$('#div').text(text);
}
```

## ¿Qué es Big O?

Big O es la abreviatura de Notación Big O.

Big O es cómo los programadores hablan sobre la escalabilidad de los algoritmos.

La Notación Big O de un algoritmo se determina por cuánto tiempo tarda el algoritmo en devolver un resultado en el **peor de los casos**.

El término matemático para el **peor de los casos** es **"cota superior"** o **"límite superior"**.

## ¿Cómo se pronuncia O(n)?

O(n) se lee como "Orden de N" o también "O de N".

La función O es la función de Orden.

## ¿Por qué se llama Big O?

Porque estamos tratando con órdenes de magnitud. Se usa `O` porque la tasa de crecimiento de una función también se conoce como el **"orden de la función"**.

## ¿Por qué es importante Big O?

Entender el Big O de los algoritmos:
* te ayudará a pensar en términos de eficiencia de código. Ej: "¡Tengo que cambiar este algoritmo porque es O(n!)!"
* te ayudará a hablar de código con otros desarrolladores. Ej: "No te preocupes, modifiqué el algoritmo para que no sea O(n²). Ahora es O(n)."
* te ayudará en las entrevistas. Podrás hablar sobre la eficiencia de los algoritmos que escribas. Ej: "Lo que acabo de codificar es O(n²)."

## Profundizando en O(1)

#### Ejemplo 2.1

```js
function returnItem(item){
	return item;
}
```

`returnItem` es una función sin mucho sentido, pero sígueme la idea.

```js
returnItem(2);
```

El Big O de `returnItem` es tiempo constante. No importa qué pasemos a `returnItem`, el algoritmo realizará una unidad de trabajo.

La "complejidad" de esta función es `O(1)`.

Si quieres graficar `O(1)`, establecerías `y` igual a 1 y lo graficarías.

**y = 1**

![o(1)](o_1__plot.png)

Observa que mientras más a la derecha vayas en el eje horizontal (eje x), el eje vertical (eje y) permanece igual.

## Profundizando en O(n)

#### Ejemplo 2.2
```js
function itemInList(check, list){
	for (var i = 0; i < list.length; i++){
		if (list[i] === check) return true;
	}
	return false;
}
```

Esto se ejecutará bastante rápido:

```js
itemInList(2, [1,2,3]);
```

La "complejidad" de `itemInList` es `O(n)`.

Esto significa que es una gráfica lineal.

Para `itemInList`, si la longitud del array es 3, en el **peor de los casos** tomará 3 unidades de trabajo.

Claro, en el mejor de los casos tomará 1 unidad de trabajo, pero la Notación Big O no trata sobre el mejor de los casos, sino sobre el **peor de los casos**.

Si quieres graficar `O(n)`, reemplazarías la `n` con una `x` y la establecerías igual a `y`.

**y = x**

![o(n)](o_n__plot.png)

Observa que mientras más a la derecha vayas en el eje horizontal (eje x), el eje vertical (eje y) también sube.

## Profundizando en O(n²)

#### Ejemplo 2.3
```js
function allCombos(list){
	var results = [];
	for (var i = 0; i < results.length; i++){
		for (var j = 0; j < results.length; j++){
			results.push([i, j]);
		}
	}
}
```

Si hacemos `allCombos([1,2,3])` obtendríamos `[(1,1) (1,2), (1,3), (2, 1), (2, 2), (2, 3), (3, 1), (3, 2), (3, 3)]`.

La "complejidad" de `allCombos` es `O(n²)`.

La longitud de la lista argumento de `allCombos` es la `n` en `O(n²)`.

allCombos([1]) -> [[1,1]]. Una unidad de trabajo.  1² = 1
allCombos([1,2]) -> [[1,1], [1,2], [2,1], [2,2]]. Cuatro unidades de trabajo. 2² = 4

Así que n * n es n².

## Comparación de O(1), O(n), O(n²)

Observa que mientras más a la derecha vayas en el eje horizontal (eje x), el eje vertical (eje y) sube más rápido para `O(n²)`, más lento para `O(n)` y se mantiene constante para `O(1)`.

Esto significa que `O(n²)` se ejecuta más lento que `O(n)`, que a su vez se ejecuta más lento que `O(1)`.

![comparison](runtime_comparison.png)

## O(1) vs O(n) vs O(n²) explicado sin código

#### O(1)
Considera la suma de un solo dígito con lápiz y papel. El tipo que aprendiste cuando eras pequeño.

```
5 + 5 = 10

3 + 3 = 6

2 + 2 = 4

2 + 3 = 5

6 + 7 = 13
```

Cada uno de esos diferentes problemas tomó la misma cantidad de operaciones para completarse (o la misma cantidad de unidades de trabajo). Tomas un número y lo sumas a otro. Listo.

Como siempre son las mismas unidades de trabajo para completar, sin importar el problema, el Big O es constante, este es un ejemplo de `O(1)`.

#### O(n)

Considera la suma de múltiples dígitos con lápiz y papel.

```
55 + 72 = 127

455 + 322 = 777

1234 + 4447 = 5681

4999 + 56 = 5055
```

Observa cómo el número de operaciones (o la cantidad de unidades de trabajo para completar) aumenta a medida que aumenta el número de dígitos.

El número de operaciones se correlaciona directamente (son uno a uno) con el número de dígitos del número más grande que se está sumando.

Esto tomaría en el peor caso `O(n)` unidades de trabajo.

#### O(n²)

Ahora, considera la multiplicación de múltiples dígitos con lápiz y papel.

```
55538 * 92338 = 5128267844
```

Esto es mucho más difícil de hacer que las dos operaciones anteriores.

Cada dígito del número inferior debe multiplicarse por cada dígito del número superior.

Si estuvieras multiplicando números de 100 dígitos entre sí, tomaría 10,000 operaciones matemáticas para completar (unidades de trabajo).

Esto tomaría en el peor caso `O(n²)` unidades de trabajo para completar.

## Profundizando en O(log(n))

O(1) < O(log(n)) < O(n) < O(n²)

![o(log n)](o_logn.gif)

#### ¿Cómo se ve un algoritmo que tiene un Big O de O(log(n))?

La elección del siguiente elemento sobre el cual realizar alguna acción es una de varias posibilidades, y solo una necesitará ser elegida.

#### Ej. Buscar personas en una guía telefónica es O(log(n))

No necesitas revisar cada persona en la guía telefónica para encontrar la correcta; en su lugar, puedes simplemente dividir y conquistar, y solo necesitas explorar una pequeña fracción de todo el espacio antes de encontrar eventualmente el número de teléfono de alguien.

Por supuesto, una guía telefónica más grande seguirá tomándote más tiempo, pero no crecerá tan rápido como el aumento proporcional en el tamaño adicional.

#### Ej. un algoritmo que tiene un Big O de O(log(n))

```js
function twoDivides(x){
	var count = 0;
	while (parseInt(x) > 1) {
		x = x / 2;
		count = count + 1;
	}
	return count;
}
```

##### Calculando el Big O del algoritmo anterior

**sin matemáticas**

A menudo no necesitas matemáticas para determinar cuál es el Big-O de un algoritmo. Puedes simplemente usar tu intuición.

Miras cuántas unidades de trabajo tiene que hacer el algoritmo a medida que crece la entrada y lo relacionas con el Big O correcto.

Sin contar el retorno o la declaración de variable:  
twoDivides(2) = 1. Las operaciones para cada paso del bucle serían x = 2/1 (para la división) y count = 0 + 1 (para el conteo); así que 2 en total.  
twoDivides(4) = 2. Las operaciones serían `x = 4/2` y `count = 0 + 1`, `2/1` y `1 + 1`; así que 4 en total.  
twoDivides(8) = 3. Las operaciones serían `x = 8/2` y `count = 0 + 1`, `4/2` y `1 + 1`, `2/2` y `2 + 1`; así que 6 en total.  
twoDivides(16) = 4. Las operaciones serían `x = 16/2` y `count = 0 + 1`, `8/2` y `1 + 1`, `4/2` y `2 + 1`, `2/2` y `3 + 1`, así que 8 en total.  
twoDivides(32) = 5. Las operaciones serían `x = 32/2` y `count = 0 + 1`, `16/2` y `1 + 1`, `8/2` y `2 + 1`, `4/2` y `3 + 1`, `2/2` y `4 + 1`; así que 10 en total.  

La "complejidad" de twoDivides es `O(log(n))`.  

n    |  operaciones
-----|---------------
2    |  2
4    |  4
8    |  6
16   |  8
32   |  10
...  | ...
n    | 2 * log(n)

`log(n)` aquí esencialmente significa "el número de veces que podemos dividir `n` por 2".

**Nota al margen:** Al escribir la Notación Big O, el "2" inicial se ignoraría - no cambia significativamente el comportamiento asintótico de la función para valores grandes de `n`. Así, podemos ver que `O(2 * log(n))` es equivalente a `O(log(n))`. En general, al escribir la notación Big O solo te preocupas por la porción más significativa de complejidad (incluso `2n² + 2n` se escribiría como `O(n²)`.
    
En este caso (`log(n)`), el tamaño del número es la `n`. Podemos ver que el número de operaciones no es constante, pero no crece linealmente (y crece más lentamente a medida que aumenta la `n`).

**caso general, con matemáticas** 

Iteración |   x
----------|--------
0         |  x (esto es lo mismo que x/1)
1         |  x/2
2         |  x/4
...       |  ...
k         |  x/2^k 

2^k = x → Aplicando logaritmo a ambos lados → k = log(x)

log(2^k) = log(x)

k*log(2) = log(x)

k = log(x)/log(2)

k aproximadamente igual a log(x)

## Profundizando en O(n log n)

O(1) < O(log(n)) < O(n) < O(n log(n)) < O(n²)

```js
// asumimos que n es un entero
function nlogn(n){
	var results = [];
	for (var i = 0; i < n; i++){ // este bucle se ejecuta n veces, así que O(n)
	    for (var j = n; j > 0; j = parseInt(j/2)){ // este bucle se ejecuta log(n) veces, así que O(logn)
	    	results.push(j);
	    }
	}
	return results;
}
```

Para bucles for adyacentes, sumarías los tiempos de ejecución, p.ej. `O(n + m)`. Para bucles for anidados, los multiplicas, p.ej. `O(n*m)`, o en este caso `O(nlogn)`.

Esto resultaría en 

```
nlogn(3)
[3, 1, 3, 1, 3, 1]
```

```
nlogn(4)
[4, 2, 1, 4, 2, 1, 4, 2, 1, 4, 2, 1]
```

## Profundizando en O(2^n)

Los algoritmos con un Big O de 2^n suelen ser recursivos.

```js
// asumimos que number es un entero
function fib(number) {
 if (number <= 1) return number;
 return fib(number - 2) + fib(number - 1);
}
```

`O(2^n)` ocurre cuando un problema de tamaño `n` requiere resolver dos problemas más pequeños de tamaño `n-1` (en fibonacci esto es casi cierto, son dos problemas, uno de tamaño `n-1` y el otro de tamaño `n-2`. En esencia, estás duplicando el número de problemas que necesitas resolver cada vez que n aumenta.

Supongamos que nuestro algoritmo toma dos operaciones, y que resolver un problema de tamaño `n` requiere resolver dos problemas de tamaño `n-1`. Entonces, el número de operaciones para valores crecientes de `n` son:

n   |  ops(n)
--- | ---
1   | 2 
2   | 4 = 2 + 2 = ops(2-1) + ops(2-1) = 2(2) = 2^2
3   | 8 = 4 + 4 = ops(3-1) + ops(3-1) = 2(4) = 2(2^2)= 2^3
4   | 16 = 8 + 8 = ops(4-1) + ops(4-1) = 2(8) = 2(2^3) = 2^4
...
k   | (k-1) + (k-1) = 2(k-1) = 2((k-2) + (k-2)) = 4(k-2) = 8(k-3) = ... = 2^(k-1)(2) = 2^k

## Profundizando en O(n!)

Cualquier algoritmo que calcule todas las permutaciones de un array dado es `O(n!)`. Factorial es el número que obtienes si multiplicas cada número desde 1 hasta `n`.

Imagina que tienes un array de palabras y quieres devolver todas las combinaciones posibles de esas palabras.

Entonces, dado
```
['apple', 'bear', 'limp bizkit']
```

El algoritmo devolvería un array de 6 arrays. Así:
```
[
	['apple', 'bear', 'limp bizkit'],
	['apple', 'limp bizkit', 'bear'],
	['bear', 'limp bizkit', 'apple'],
	['bear', 'apple', 'limp bizkit'],
	['limp bizkit', 'bear', 'apple'],
	['limp bizkit', 'apple', 'bear'],
]
```
Escribir un algoritmo que hiciera eso sería `O(n!)`. `n` aquí es la longitud del array, así que 3! = 3 * 2 * 1 = 6. 

Otro ejemplo:

```js
// asumimos que n es un entero
function nFactorial(n) {
  for (var i = 0; i < n; i++) {
    return nFactorial(n - 1);
  }
}
```

Esto ejecuta la función `nFactorial` `n-1` veces para una entrada `n`. Así, obtienes `n*nFactorial(n-1)`.

`n*f(n-1) = n*(n-1)*f(n-2) = ... = n*(n-1)*(n-2)*...*1*f(1) = n!`.

## Big O puede ser engañoso

La notación Big-O es una estimación y solo es útil para valores grandes de n.

#### ordenación por inserción vs ordenación por fusión

El tiempo de ejecución en el peor de los casos para el **algoritmo de ordenación por inserción es O(n²)**.

En relación con Big O, eso es peor que el tiempo de ejecución para la **ordenación por fusión, que es O(n log n)**.

¡Pero para pequeñas cantidades de datos (cuando n es pequeño), la ordenación por inserción es en realidad más rápida, especialmente si el array ya está parcialmente ordenado!

Big O es útil cuando se comparan dos algoritmos para determinar cuál se ejecuta más rápido cuando n es grande.

Si la cantidad de datos (n) es relativamente pequeña, entonces incluso un algoritmo lento será lo suficientemente rápido para uso práctico.

#### Otras consideraciones

El tiempo de ejecución promedio de los algoritmos puede variar significativamente para diferentes entradas, pero la notación Big O solo indica el peor de los casos. Así, puedes tener un algoritmo que se ejecuta en `logn` en el 99% de los casos, pero el 1% del tiempo toma tiempo `n!`, y otro que resuelve el mismo problema pero siempre se ejecuta en `n²`. Por lo tanto, la notación Big O no da la imagen completa de la eficiencia del tiempo de ejecución. Esto es particularmente notable al observar algoritmos de ordenación, que tienen diferentes tiempos de ejecución en el mejor, peor y caso promedio. Sin embargo, la mayoría de las discusiones sobre análisis de tiempo de ejecución se centran en Big O y el tiempo de ejecución en el peor de los casos.

## Otras categorías de Big O de más rápida a más lenta

Big-O | Nombre | Descripción
------| ---- | -----------
**O(1)** | constante | **Esta es la mejor.** El algoritmo siempre toma la misma cantidad de tiempo, independientemente de cuántos datos haya. En otras palabras, el número de unidades de trabajo que le toma al algoritmo completarse es independiente del tamaño de la entrada. Ejemplo: buscar un elemento de un array por su índice.
**O(log n)** | logarítmico | **Bastante bueno.** Este tipo de algoritmos elimina un porcentaje de la cantidad de datos a revisar con cada iteración. Si tienes 100 elementos, toma alrededor de 7 pasos encontrar la respuesta. Con 1,000 elementos, toma 10 pasos. Y 1,000,000 de elementos solo toman 20 pasos. Esto es súper rápido incluso para grandes cantidades de datos. Ejemplo: búsqueda binaria (búsqueda en array ordenado).
**O(n)** | lineal | **Buen rendimiento.** Si tienes 100 elementos, esto hace 100 unidades de trabajo. Este es usualmente el caso para un bucle. Si duplicas el tamaño de n, entonces el algoritmo hace 2 * n unidades de trabajo. Ejemplo: búsqueda en array no ordenado.
**O(n log n)** | "linearítmico" | **Rendimiento decente.** Esto es ligeramente peor que lineal pero no demasiado malo. Ejemplo: mergesort y otros algoritmos de ordenación "rápidos".
**O(n²)** | cuadrático | **Algo lento.** Si tienes 100 elementos, esto hace 100² = 10,000 unidades de trabajo. Duplicar el número de elementos lo hace cuatro veces más lento (porque 2 al cuadrado es igual a 4). Ejemplo: un doble bucle for -> tienes que mirar cada par de elementos de entrada.
**O(n³)** | cúbico | **Rendimiento pobre.** Si tienes 100 elementos, esto hace 100³ = 1,000,000 unidades de trabajo. Duplicar el tamaño de entrada lo hace ocho veces más lento. Ejemplo: multiplicación de matrices. O estás mirando cada par de entradas pero la operación que haces requiere mirar todas las entradas nuevamente.
**O(2^n)** | exponencial | **Rendimiento muy pobre.** Quieres evitar este tipo de algoritmos, pero a veces no tienes opción. Agregar solo un bit a la entrada duplica el tiempo de ejecución. Ejemplo: adivinar por fuerza bruta los resultados de una secuencia de `n` lanzamientos de moneda.
**O(n!)** | factorial | **Intolerablemente lento.** Literalmente toma un millón de años hacer cualquier cosa. Ejemplo: necesitas considerar cada posible subconjunto de tus entradas. Echa un vistazo al problema del vendedor viajero - forzar una solución para ello es `n!`.

![o(n)](most-of-them.png)

## otra tabla

Big-O | cálculos para 10 elementos | cálculos para 100 elementos
------| ---- | -----------
O(1)        |   1                         |     1
O(log(n))   |   3                         |     7
O(n)        |  10                         |   100
O(n log(n)) |  30                         |   700
O(n²)      | 100                         | 10000
O(n³)      | 1000                         | 1000000
O(2^n)      | 1024                         | 2^100
O(n!)      | 3628800                         | 100! -> matemáticamente esto es el producto de (100 * 99 * 98...)

## y otra más

n   | logn | n  | nlogn | n² | 2^n | n!
--- | ---  |--- | ---   |---  | --- | ---
1   | 0    | 1  | 0     | 2   | 2   | 1
2   | 3.69 | 2  | 1.4   | 4   | 4   | 2
3   | 1.1  | 3  | 3.3   | 9   | 8   | 6
4   | 1.4  | 4  | 5.5   | 16  | 16  | 24
5   | 1.6  | 5  | 8     | 25  | 32  | 120
10  | 2.3  | 10 | 23    | 100 | 1024| 3628800 


## Cuestionario

¿Cuál es el Big O de cada uno de estos algoritmos?

a)

```js
function countUpA(n){
	var count = 0;
    for (var i = 1; i <= n; i++) {
        for (var j = n; j > 1; j--) {
            for (var k = 1; k < n; k = k + 2) {
                count++;
            }
        }
    }
    return count;
}

```

b)
```js
function countUpB(n){
	var count = 0;
	for (var i = 1; i <= n; i++) {
	    for (var j = n; j > 1; j--) {
	        for (var k = 1; k < 1000; k = k + 2) {
	            count++;
	        }
	    }
	}
	return count;
}

```

c)
```js
function countUpC(n){
	var count = n;
	for (var i = 1; i <= 1000000; i++) {
	    for (var j = i; j > 500; j--) {
	        for (var k = 1; k < 10500; k = k + 2) {
	            count++;
	        }
	    }
	}

	return count;
}

```
d)

```js
function countUp(n){
	var count = 0;
	var j = 1;
	for (var i = 1; i < n; i++) {
        while (j < n) {
            j++;
            count++;
        }
        j = 1;
	}
	return count;
}

```

e)

```js
function countUpE(n){
	var count = 0;
	var i = n;
	while (i > 1){
	    count++;
	    i = i / 2;
	}
	return count;
}

```


## Respuestas al Cuestionario

a) O(n³)

Triple bucle for, a medida que la entrada crece, las unidades de trabajo crecen a un ritmo cúbico.

b) O(n²)

Triple bucle for, pero solo 2 de los bucles for aumentan las unidades de trabajo respecto a la entrada.

c) O(1)

A medida que la entrada crece, las unidades de trabajo siempre se mantienen iguales.

d) O(n²)

A medida que la entrada crece, las unidades de trabajo aumentan a un ritmo cuadrático.

e) O(log n)

A medida que la entrada crece, las unidades de trabajo aumentan, pero no a un ritmo lineal o cuadrático.



## Recursos utilizados

Explicaciones:
https://justin.abrah.ms/computer-science/big-o-notation-explained.html
http://stackoverflow.com/questions/107165/big-o-for-eight-year-olds?rq=1

Ejemplos de código reelaborados de aquí:
http://stackoverflow.com/questions/17122807/big-o-ologn-code-example
http://stackoverflow.com/questions/19021150/big-oh-for-n-log-n

Gráficos/Imágenes utilizadas:
https://github.com/raywenderlich/swift-algorithm-club/blob/master/Big-O%20Notation.markdown
https://www.quora.com/How-would-you-explain-O-log-n-in-algorithms-to-1st-year-undergrad-student
http://www.daveperrett.com/articles/2010/12/07/comp-sci-101-big-o-notation/

Cuestionario:
http://stackoverflow.com/questions/9223351/confused-on-big-o-notation?rq=1