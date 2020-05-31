# ![Funciones _First-Class_](https://i.imgur.com/YI8MBz0.png)

<div align="center">  
  <p align="center">
  <sub>Hola! Soy Nico (<strong>nhsz</strong>), <strong>Dev Full Stack JavaScript y mentor</strong>.</sub>
  </p>
  
  <p align="center">
    <sub>
      Hace un tiempo (principios de 2019) empecé un proyecto llamado <a href="https://undefinedschool.io"><strong>undefined school</strong></a>, una <strong>escuela de Desarrollo Web Full Stack JavaScript</strong>, 100% Open Source, con mentorías personalizadas para grupos reducidos y el foco puesto en los <strong>fundamentos</strong> y <strong>conceptos avanzados</strong>.
    </sub>
  </p>

  <p align="center">
    <sub>
      Me interesa mucho la intersección entre la educación y la tecnología, por eso también participo en proyectos como <a href="https://freecodecampba.org">freeCodeCampBA</a> (co-founder y co-organizador) y <a href="https://twitter.com/LXBA_">Learning Experience BA</a> (co-founder y co-organizador).
    </sub>
  </p>

 <p align="center">
    <sub>
  👉 Si estás arrancando en el mundo del desarrollo web y necesitás una mano, podés encontrarme en <a href="https://twitter.com/_nhsz/">Twitter</a> (también para hablar sobre cualquier tema relacionado a JavaScript o <em>#nerdeadas</em> en general 😛).
  </sub>
  </p>
  
  <p align="center">
  <sub>
    Por último, te cuento que soy muy fan del café (obvio que negro y sin azúcar), asi que si las notas te resultaron útiles y querés colaborar para que no me quede dormido y siga escribiendo guías, apuntes y más <strong>contenido Open Source en español</strong>, podés invitarme uno, gracias! ❤️
  </sub>
  </p>
  
  <p align="center">
  ☕
  <code> 
  <a href="https://cafecito.app/nhsz">
    <strong>Invitame 1 café!</strong>
  </a>
  </code>
  </p>
  <hr>
</div>

👉 Ver [todas las notas](https://github.com/undefinedschool/notes)

## Contenido

- [Intro](https://github.com/undefinedschool/notes-functions-first-class#intro)
- [Alto orden!](https://github.com/undefinedschool/notes-functions-first-class#alto-orden)
- [¿Por qué podemos tratar a las funciones como cualquier otro valor?](https://github.com/undefinedschool/notes-functions-first-class#por-qu%C3%A9-podemos-tratar-a-las-funciones-como-cualquier-otro-valor)
- [Ejemplos](https://github.com/undefinedschool/notes-functions-first-class#ejemplos)
  - [Asignar una función a una constante/variable](https://github.com/undefinedschool/notes-functions-first-class#asignar-una-funci%C3%B3n-a-una-constantevariable)
  - [Pasar una función por parámetro](https://github.com/undefinedschool/notes-functions-first-class#pasar-una-funci%C3%B3n-por-par%C3%A1metro)
  - [Retornar una función](https://github.com/undefinedschool/notes-functions-first-class#retornar-una-funci%C3%B3n)
  - [Como _propiedades_ de un objeto,aka _métodos_](https://github.com/undefinedschool/notes-functions-first-class#como-propiedades-de-un-objetoaka-m%C3%A9todos)
  - [Array de funciones](https://github.com/undefinedschool/notes-functions-first-class#array-de-funciones)
  - [Usando _IIFEs_](https://github.com/undefinedschool/notes-functions-first-class#usando-iifes)
  - [Usando el constructor _Function_](https://github.com/undefinedschool/notes-functions-first-class#usando-el-constructor-function)

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
