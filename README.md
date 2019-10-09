> El siguiente contenido fue elaborado por [@_nhsz](https://twitter.com/_nhsz) como guía para las clases de [undefined school](https://twitter.com/undefinedSchool)

> Son bienvenidos los _issues_ y _PRs_ para mejorar el contenido, corregir errores, etc

> Si el contenido te resultó útil y querés colaborar, podés hacerlo [acá](https://trello.com/c/TFbCZtPN/34-donaciones) (se acepta BTC :P). Gracias!

# ✨ Las funciones en JavaScript son _First-Class citizens_

Un lenguaje de programación tiene _First-Class functions_ cuando **las funciones puede ser tratadas como cualquier otro valor**. Es decir, podemos:
  - Asignarlas como valores a una variable o constante
  - Recibirlas como parámetro (_callbacks_) :star:
  - Retornar funciones :star:

- El truco es olvidarte por un rato que estás tratando con funciones, pensá que se trata de un valor cualquiera, como un `number`, `string` ó `boolean`y qué cosas podés hacer con este.

## Alto orden!

Las características anteriores, marcadas con :star: hacen que una función sea además lo que se conoce como _función de alto orden_ ó _Higher Order Function_ :sunglasses:

Para más detalles, ver [MDN: First Class Function](https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function)

## ¿Por qué podemos tratar a las funciones como cualquier otro valor?

Porque las funciones en JS... [**son objetos!**](https://github.com/undefinedschool/notes-oop-js/blob/master/README.md#las-funciones-son-funciones-y-objetos)

## Ejemplos

### Asignar una función a una constante/variable (se acuerdan de las _function expressions?_)

```js
const fn = function() {
  // do smth
}

fn();
```

### Pasar una función por parámetro

```js
function calc(x, y, fn) {
  fn(x, y);
}
```

### Retornar una función

```js
function hof(fn) {
  return fn;
}
```

### Array de funciones

Si un _array_ puede guardar valores de cualquier tipo, entonces también podemos guardar funciones, no? Obvio 🎉 (alguien dijo _React Hooks_? 😛)

```js
const functionsList = [() => console.log('Hello'), (a, b) => a + b]

functionsList[0]() // 'Hello';
functionsList[1](3, -27) // => -24;
```

### Usando [IIFEs](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)

```js
console.log(7 + 21) // 28
console.log(7 + (function() { return 21; })()) // 28
```
