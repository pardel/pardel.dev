---
description: global and local scopes.
---

# Scope

## **Vars**

**Var**s are defined in the global scope and can be redefined in the current scope. Notice that the `foo` inside the `hello()` function doesn't impact the global `foo` but the one inside the `if` block does:

```javascript
var foo = "a";
var foo = "b";
console.log(`Global Scope: ${foo}`);
>> Global Scope: b

function hello(){
  var foo = "d";
  console.log(`Function Scope: ${foo}`);
}
hello();
>> Function Scope: d

console.log(`Global Scope: ${foo}`);
>> Global Scope: b

if (true) {
  var foo = "d";
  console.log(`If Scope: ${foo}`);
}
>> If Scope: d

console.log(`Global Scope: ${foo}`);
>> Global Scope: d

```

## **Let**

**Let**s exist in current scope and can't be redefined:

```javascript
‣ let foo = "a";
‣ let foo = "b";
SyntaxError: redeclaration of let foo
```

## Function scope

```javascript
var foo = "a";
let bar = "b";
const baz = "c";
console.log(`Global Scope: ${foo}, ${bar}, ${baz}`);

    Global Scope: a, b, c

‣ function hello(){
    var foo = "d";
    let bar = "e";
    const baz = "f";
    console.log(`Function Scope: ${foo}, ${bar}, ${baz}`);
  }
‣ hello();
    Function Scope: d, e, f

‣ console.log(`Global Scope: ${foo}, ${bar}, ${baz}`);
    Global Scope: a, b, c
```

## Block scope

```javascript
‣ var foo = "a";
‣ let bar = "b";
‣ const baz = "c";
‣ console.log(`Global Scope: ${foo}, ${bar}, ${baz}`);
    Global Scope: a, b, c

‣ if (true) {
    var foo = "d";
    let bar = "e";
    const baz = "f";
    console.log(`If Scope: ${foo}, ${bar}, ${baz}`);
  }
    If Scope: d, e, f

‣ console.log(`Global Scope: ${foo}, ${bar}, ${baz}`);
    Global Scope: d, b, c
```

## Variable Hoisting

**Var**s declarations are "moved" to the top of their scope:

```javascript
‣ function hello() {
    console.log(answer);
    var answer = 43;
    console.log(answer);
  }

undefined
43
```

**NB:** only the declaration is moved and not the assignment!

Things are different for **let**: although also defined outside `hello()`, `answer` is not available inside the function before being declared - the second `answer` is defined in a **local** scope, a _function scope._ The hoisting doesn’t occur.

```javascript
‣ let answer = 42;
‣ function hello() {
    console.log(answer);
    let answer = 43;
  }

Uncaught ReferenceError: answer is not defined at 
  hello (<anonymous>:2:17) at <anonymous>:1:1
```

## Functions Hoisting

Functions are automatically hoisted and made available:

```javascript
‣ hello();

function hello() {
   ...
}
```

