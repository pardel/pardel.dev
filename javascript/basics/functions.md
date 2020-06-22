# Functions

"In JavaScript, functions are **first-class objects**, because they can have properties and methods just like any other object. What distinguishes them from other objects is that **functions can be called**. In brief, they are [`Function`](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Function) objects."

\(from [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions)\)

## function statement

```javascript
‣ function hello(audience){
    console.log(`Hello ${audience}`);
  }
‣ hello("World");
  Hello World
```

##  function expression

Anonimous function:

```javascript
‣ const hello = function(audience) {
    console.log(`Hello ${audience}!`);
  }
‣ hello("Paul");
  Hello Paul!


```

Named function:

```javascript
‣ const hello = function sayHello(audience) {
    console.log(`Hello ${audience}!`);
  }
‣ hello("Paul");
  Hello Paul!
‣ sayHello("Paul")
  ReferenceError: sayHello is not defined
```

So since `sayHello` is not defined, why use it? It help with debugging - the stack trace will include the function name. 

ES6 compliant engines support function name inference, so expressions like `var hello = function() {}` will result in named function expressions automatically.

## Shorthand method definition

```javascript
const person = {
    name:"Paul", 
    location:"London",
    hello() {
      console.log(`Hello ${this.name}`);
    }
  }
  
‣ person.hello
  function hello()
```

## Arrow functions

An **arrow function expression** is a syntactically compact alternative to a regular [function expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function), although without its own bindings to the [`this`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this), [`arguments`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments), [`super`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super), or [`new.target`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new.target) keywords.

```javascript
‣ const countries = [
    {name: 'UK', capital: 'London'},
    {name: 'France', capital: 'Paris'}
  ]

‣ countries.map(function(country) {
    return country.capital;
  });
Array [ "London", "Paris" ]

‣ countries.map((country) => {
    return country.capital;
  });
Array [ "London", "Paris" ]
```

Define our own:

```javascript
‣ const absValue = (number) => {
    if (number < 0) {
      return -number;
    }
    return number;
  };

‣ console.log(absValue(-10));
10
```

## `Function` constructor

```javascript
‣ const hello = Function('console.log("Heya!");');
‣ hello();
Heya!

‣ console.log(hello.name);
anonymous


```

Function created with the `Function` constructor **don't** create closures to their creation contexts: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function)

## \*\*\*\*[**IIFE**](https://developer.mozilla.org/en-US/docs/Glossary/IIFE) \(Immediately Invoked Function Expression\)

Used when a function will only be invoked once:

```javascript
‣ (function () {
    console.log("Hello World!");
  })();
  Hello World!
```



