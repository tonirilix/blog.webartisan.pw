---
draft: false
date: 2020-01-22T23:01:39-06:00
title: "Programando un algoritmo en silencio 001 - Balanced Brackets"
slug: "2020/01/22/algoritmo-en-silencio-001" 
tags: ["algoritmo", "algo in silence", "algoritmo en silencio","estructura de datos", "coding interview", "HackerRank"]
categories: ["coding challenge", "algoritmos", "coding interview"]
description: "¿Cómo resolver el challenge Balanced Brackets?"
---
Resolver un Coding Challenge mediante algún algoritmo y/o estructura de datos no siempre es tarea fácil. Requiere de mucha práctica y también de aprender de otras personas que se dedican a esto y, que son tan amables de subir tanto sus versiones de código como el porqué de los mismos.
En lo personal nunca me he considerado bueno haciendo este tipo de ejercicios, pero poco a poco y a base de práctica les he perdido el miedo.

Implementar algoritmos y estructuras para resolver estos ejercicios se llega a tornar muy divertido y a veces hasta adictivo. 
Después de cierto tiempo de práctica, tu lógica se ve incrementada; las habilidades adquiridas te harán ver patrones en problemas de tu día a día, permitiendo implementar soluciones de código más elegantes. 

Los algoritmos y estructuras de datos son pieza fundamental en muchas entrevistas para conseguir empleo como Ingeniero de Software. La razón es que ayuda al entrevistador a ver tu capacidad de resolución de problemas y la complejidad a la que estás acostumbrado resolver. 

Últimamente hay disputas al respecto, ya que varias personas en la industria (incluyéndome) consideran que 30 minutos de código no deberían definir qué tan bueno o malo eres. Aún así, este tipo de exámentes se siguien realizando en grandes empresas por lo que no hay más opción que practicar y practicar y seguir practicando.


## Balanced Brackets
Este fue de mis primeros ejercicios, mismo que me parece muy interesante. 
El ejercicio fue tomado de [HackerRank](https://www.hackerrank.com/challenges/ctci-balanced-brackets/problem) y tiene una calificación de Dificultad *Media* según el mismo sitio.

### El problema

Un bracket puede ser entendido como uno de los siguientes caracteres: (, ), {, }, [, o ].

Se considera que dos brackets hacen match si un bracket de apertura (ej. (, [, o {) ocurre a la izquierda de un bracket de cierre (ej. ), ], o }) del mismo tipo. Hay 3 tipos de pares que hacen match: [], {}, y ().

Un par de brackets no es balanceado si el conjunto de brackets al que encierra no hacen match.

### Ejemplos de brackets balanceados y no balanceados
- {[(])} No balanceado
- {[([)} No balanceado
- []{}() Balanceado
- [({})]{}() Balanceado
- ({(){}[]})[] Balanceado
- {{[[(())]]}} Balanceado

### ¿Qué se espera de la solución?
Se requiere que por cada expresión validada se indique si está balanceada o no.

## Cómo comenzar a practicar 
Cuando comencé a tratar de resolver Coding Challenges traté de hacerlo sin mirar ninguna solución de alguien más. Pero me bloqueaba mucho ya que mi solución casi siempre era hacerlo por fuerza bruta; muchos ciclos y muchas condiciones. Esto no es del todo malo pero también tomé el consejo que siempre doy a personas que están aprendiendo culaquier cosa: 

> "Comienza con lo que te divierta, comienza con curiosidad - Ben Lesh"

Los algoritmos y estructuras de datos no son algo nuevo, hay mucha documentación sobre el cómo realizar ordenamientos, una pila, una cola, un hashmap... incluso hay lenguajes de programación que ya tienen dichas estructuras, métodos de ordenamiento, etc., en el core de los mismos. 

Es algo muy importante de aprender en ingeniería de software, pero es posible que el hecho de entenderlos no te hará identificar el cuándo uno u otro. Al menos así es como sucedió conmigo.

HackerRank en cada uno de sus ejercicios contiene una sección de foro, en donde otras personas conversan sobre posibles soluciones y el porqué de los mismos. Esta es una sección que me fue de mucha ayuda ya que, gracias a las discusiones que ahí encontré, pude ir conectando el cómo usar las estructuras y poco a poco comencé a ver patrones en nuevos ejercicios. 

El foro de este challenge se encuentra en la siguiente liga: [Foro Balanced Brackets](https://www.hackerrank.com/challenges/ctci-balanced-brackets/forum)

## Solución Versión 1
Mi primera solución lucía así:

```js
function isBalanced(expression){
    /*
     * Parte 1:
     * Convierte el string en un array por cada elemento
     * Ej.: 
     * "[]{}()" se convertiría a ["[", "]", "{", "}", "(", ")"]
     */
    const array = expression.split(''); 

    /* 
     * Parte 2:
     * El array de JS puede funcionar como una pila o como una cola dependiendo
     * del cómo uses sus métodos. En este caso lo usaremos como una pila.
     */
    const stack = [];

    /*
     * Parte 3:
     * Por cada elemento en el array revisamos si 
     * es un bracket de apertura, en ese caso
     * Agregamos a la pila el bracket de cierre.
     * Ej.: Para el elemento "{" guardamos "}"
    */
    for(let c of array){
        if(c === '{'){
            stack.push('}');
        } else if( c === '[' ){
            stack.push(']');
        } else if( c === '(' ){
            stack.push(')');
        } else {
            /*
             * Parte 4:
             * En caso de que no sea un elemento de apertura, revisamos
             * el último elemento en la pila para ver si coincide con el elemento 
             * en el ciclo actual.
             */
            let isEmpty = stack.length === 0;
            const matchesTop = stack[stack.length - 1] === c;
            // Si no coincide entonces sabemos que no está balanceado
            // y salimos del ciclo.
            if(isEmpty || !matchesTop){
                return false;
            }
            // Caso contrario sacamos ese elemento de la pila
            stack.pop();
        }        
    }

    /*
     * Si la pila está vacía entonces sí está balanceado
     */
    let isEmpty = stack.length === 0;
    return isEmpty;
}
```

No está mal a decir verdad ya que pasa todos los casos de prueba y, hace uso de la estructura de datos llamada pila.

### Explicación versión 1
Considero conveniente explicar más a detalle la parte 3 ya que es donde sucede la magia.

En cada ciclo se trata de ir revisando únicamente brackets de apertura y, en caso de que exista, se guarda en la pila su elemento de cierre.
Pongamos un ejemplo sencillo.

**Expresión 1: [({})]**

Los tres primeros elementos son todos brackets de apertura, por lo que la pila comenzaría así: 

| Elemento  | Posición |
| --------- | -------- |
|     }     |     2    |
|     )     |     1    |
|     ]     |     0    |

Recordemos que una pila funciona "El último en entrar es el primero en salir" (_LIFO_ por sus siglas en inglés). Por lo que para el cuarto el ciclo entraría en la parte 4 del código:

`const matchesTop = stack[stack.length - 1] === c;`

- `stack[stack.length - 1]` apunta al último elemento en la pila
- `c` apunta al elemento actual en el ciclo

Donde 

| Expresión               | Valor |
| ----------------------- | ----- |
|            c            |   }   |
| stack[stack.length - 1] |   }   |

Entonces `matchesTop` sería `true` y sacaríamos el último elemento de la pila, así: 

| Elemento  | Posición |
| --------- | -------- |
|     )     |     1    |
|     ]     |     0    |

Para el quinto el ciclo entraría en la parte 4 del código:

`const matchesTop = stack[stack.length - 1] === c;`

Donde 

| Expresión | Valor |
| --------- | ----- |
| c | ) |
| stack[stack.length - 1] | ) |

Entonces `matchesTop` sería `true` y sacaríamos el último elemento de la pila, así: 

| Elemento  | Posición |
| --------- | -------- |
|     ]     |     0    |

Para el quinto y último el ciclo entraría en la parte 4 del código:

`const matchesTop = stack[stack.length - 1] === c;`

Donde 

| Expresión | Valor |
| --------- | ----- |
| c | ] |
| stack[stack.length - 1] | ] |

Entonces `matchesTop` sería `true` y sacaríamos el último elemento de la pila, quedando la pila vacía. Saldríamos del ciclo de la parte 3 del código y ahora validaríamos como sigue: 

```js
let isEmpty = stack.length === 0;
return isEmpty;
```
Esta condición sería true y diríamos que la pila está balanceada. 

En la parte 4 del código hay una validación adicional en la que revisamos si para ese momento la pila ya se vació por completo, si ese es el caso, la pila tampoco estaría balanceada ya que aún tenemos un elemento en el ciclo actual, el cual estamos tratando de comparar.

Así, en la parte 4, si el stack es vacío o el último elemento agregado a la pila no coincide con el del ciclo actual, significa que la expresión no está balanceada y es mejor salir del ciclo.

Esta solución resuelve el problema, pero aún hay adecuaciones que se pueden hacer, mismas de las que hablaremos en la versión 2 del código:


### Explicación versión 2

En la versión 2, la lógica es la misma, pero se pasaron los brackets de apertura y cierre a un diccionario, esto hace más legible el código. También lo hace más mantenible, ya que si queremos agregar más brackets a la lista para ser comparados bastaría con agregarlo al diccionario.

Este diccionario se usa en el primer `if` y se reemplaza el resto de condiciones de la Parte 3 de la versión 1 ya que la lógica es la misma para todos los casos.

```js
const isBalanced = (expression) => {
    const stack = [];
    const dictionary = {
        '{': '}',
        '[': ']',
        '(': ')'
    }; 

    for(let bracket of expression){
        if(dictionary[bracket]){
            stack.push(dictionary[bracket])
        } else if(bracket !== stack.pop()){
            return false;
        }  
    }
    return stack.length === 0;
}
```

Otra modificación importante es el correcto nombramiento de variables, como el caso de la variable `c` de la versión 1, ahora se llama bracket. Es importante nombrar correctamente las variables para que cada línea código te de a entender lo que está sucediendo sin necesidad de revisar de dónde viene una variable. 

Se removió también la validación de empty stack de la parte 4 de la versión 1, esto es debido a que en Javascript, `stack.pop()` regresa `undefined` cuando el array ya no tiene elementos. 

Así también se removió el código en donde hacíamos un peek del último elemento en la pila `stack[stack.length - 1]`, esto fue gracias a que stack.pop(), además de sacar el último elemento también lo regresa. Así es como podemos comparar `bracket !== stack.pop()`. Esta condición será true para el caso en que el último elemento sea diferente al del ciclo actual, así como cuando el array ya está vacío. En ambos casos nos saldríamos de la función isBalanced por completo.

La última condición se mantiene. La validación de que el stack esté vacío es la única fuente que tenemos para saber si la expresión está balanceada.

