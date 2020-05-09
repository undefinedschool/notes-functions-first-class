# ![Funciones _First-Class_](https://i.imgur.com/YI8MBz0.png)

<div align="center">  
  <p align="center">
  <sub>
    Estas notas fueron elaboradas por <a href="https://twitter.com/_nhsz" target="_blank" rel="noreferrer noopener">@_nhsz</a>, como parte del contenido de los cursos de <a href="https://undefinedschool.io/" target="_blank" rel="noreferrer noopener"><strong>undefined school</strong></a>, una escuela de <strong>Desarrollo Web Full Stack JavaScript</strong>, <a href="https://github.com/undefinedschool/" target="_blank" rel="noreferrer noopener">100% Open Source</a>, con <strong>mentorías personalizadas para grupos reducidos</strong> y el foco puesto en los <strong>fundamentos</strong> y <strong>conceptos avanzados</strong> ⚡
  </sub>
  </p>
  
  <p align="center">
  <sub>
    Si te resultaron útiles, te cuento que soy muy fan del café; si querés colaborar para que no me quede dormido y siga escribiendo guías, apuntes y más <strong>contenido Open Source en español</strong>, podés invitarme uno, gracias! ❤️
  </sub>
  </p>
  
  <h3 align="center">
  ☕ 
  <a mp-mode="dftl" href="https://www.mercadopago.com.ar/checkout/v1/redirect?pref_id=243772354-b32a750f-2505-41c1-8e5e-9dcdb4536593" name="MP-payButton" class='blue-ar-l-rn-none'>
    <strong>Invitame 1 café!</strong>
  </a>
  </h3>
  <hr>
</div>

## Intro

Un lenguaje de programación tiene _First-Class functions_ cuando **las funciones puede ser tratadas como cualquier otro valor**. Es decir, podemos:
  - Asignarlas como valores a una variable o constante
  - Recibirlas como parámetro (_callbacks_) :star:
  - Retornar funciones :star:

- El truco es olvidarte por un rato que estás tratando con funciones, pensá que se trata de un valor cualquiera, como un `number`, `string` ó `boolean`y qué cosas podés hacer con este. 

## Alto orden!

Las características anteriores, marcadas con :star: hacen que una función sea además lo que se conoce como **_función de alto orden_ ó _Higher Order Function_** :sunglasses:

Para más detalles, ver [MDN: First Class Function](https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function)

## ¿Por qué podemos tratar a las funciones como cualquier otro valor?

Porque las funciones en JS... [**son objetos!**](https://github.com/undefinedschool/notes-oop-js/blob/master/README.md#las-funciones-son-funciones-y-objetos)

## Ejemplos

### Asignar una función a una constante/variable

Un valor cualquiera puede ser guardado en una variable/constante. ¡Una función también! 😸

Cuando asignamos una función a una variable ó constante, la llamamos [_function expression_](https://developer.mozilla.org/en-US/docs/web/JavaScript/Reference/Operators/function)

```js
// assign a number to a constant
const theNumberOfTheBeast = 666;

// assign a function to a constant
const fn = function() {
  console.log(I'm a function expression! 😎`);
}

fn();
```

### Pasar una función por parámetro

```js
const numbers = [1, 2, 3, 4, 5];

// .map() method receives a function as a parameter (callback)
numbers.map(number => number ** 2); // => [1, 4, 9, 16, 25]
```

### Retornar una función

```js
function hof(fn) {
  return fn;
}
```

### Como _propiedades_ de un objeto,aka _métodos_

```js
const hero = {
  name: 'Jessica Jones',
  quote: () => console.log(`There's dirt everywhere... you just have to know where to look`)
};

hero.quote();
```

### Array de funciones

Si un _array_ puede guardar valores de cualquier tipo, entonces también podemos guardar funciones, no? Obvio 🎉 (alguien dijo [_React Hooks_](https://medium.com/@ryardley/react-hooks-not-magic-just-arrays-cd4f1857236e)? 😛)

```js
const functionsList = [() => console.log('Hello'), (a, b) => a + b];

functionsList[0]();       // 'Hello'
functionsList[1](3, -27); // => -24

// running all of them
for (const fn of functionsList) {
  fn(1, 3);
}
```

### Usando [IIFEs](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)

Podemos crear funciones e invocarlas inmediatamente

```js
console.log(7 + 21);                            // 28
console.log(7 + (function() { return 21; })()); // => 28
```

### Usando el constructor _Function_

[**Las funciones en JavaScript son objetos**](https://github.com/undefinedschool/notes-oop-js/blob/master/README.md#las-funciones-son-funciones-y-objetos), por lo que pueden crearse como cualquier otro

```js
const sum = new Function('a', 'b', 'return a + b');

console.log(sum(2, 6)) // => 8;
```
