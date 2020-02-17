---
description: Exploring the different ways of defining variables.
---

# var, let, & const

## var

"Legacy" keyword to add a "global variable". They are declared in the global scope regardless where the actual declaration occurs - this is called variable hoisting in the JavaScript world. These variable are also made available as property to the window object \(the default context\).

```javascript
‣ var answer = 42;
‣ console.log(answer);
  42
‣ console.log(this.answer);
  42
‣ console.log(window.answer);
  42
```

Moreover, these variables are made available \(although undefined\) before their declaration. 🤯

**Notice the 2 output messages:**

```javascript
‣ var hello = function() {
    console.log(message);
    var message = "Hello there";
    console.log(message);
  };
‣ hello();
  undefined
    42
```

**"Behind the scenes", this happens:**

```javascript
‣ var hello = function() {
    var message;
    console.log(message);
    message = "Hello there";
    console.log(message);
  };
```

## let

The new way to define a variable.

```javascript
‣ let answer = 42;
‣ console.log(answer);
  42
‣ console.log(this.answer);
  undefined
‣ console.log(window.answer);
  undefined
```

```javascript
‣ function hello() {
      let answer = 42;
      console.log(answer);
  }
‣ hello();
  42

‣ function hello() {
      let answer = 42;
      console.log(this.answer);
  }
‣ hello();
  undefined
```

## const

Create a constant - once defined, it cannot be re-assigned a value.

**Cannot be re-assigned a value.**

```javascript
‣ const answer = 42;
‣ answer = 43;
  Uncaught TypeError: 
  Assignment to constant variable.
```

**Cannot be declared without a value.**

```javascript
‣ const answer;
  Uncaught SyntaxError: 
  Missing initializer in const declaration
```

#### For reference types, only the reference is a constant and not the content.

**Can reassign constant object properties but not the object itself.**

```javascript
‣ const person = { name: "John", age: 24};
‣ console.log(person);
  {name: "John", age: 24}
  
‣ person.name = "Paul";
‣ console.log(person);
  {name: "Paul", age: 24}
  
‣ person = {name: "George", age: 20}
  Uncaught TypeError: 
  Assignment to constant variable.
```

**Same applies to array, themselves objects.**

```javascript
‣ const beatles = ["John", "Paul", "George"];
‣ console.log(beatles);
  (3) ["John", "Paul", "George"]
  
‣ beatles.push("Ringo");
  4
‣ console.log(beatles);
  (4) ["John", "Paul", "George", "Ringo"]
  
‣ beatles = ["John", "Paul", "George", "Ringo", "Brian"];
  Uncaught TypeError: 
  Assignment to constant variable.
```

## Scope

```javascript
‣ var foo = "a";
‣ let bar = "b";
‣ const baz = "c";
‣ console.log(`Global Scope: ${foo}, ${bar}, ${baz}`);
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

## Scope conflict 

Danger!!!

```javascript
‣ let answer = 42;
‣ function hello() {
    console.log(answer);
  }

42
```

```javascript
‣ let answer = 42;
‣ function hello() {
    let answer = 43;
    console.log(answer);
  }

43
```

```javascript
‣ let answer = 42;
‣ function hello() {
    console.log(answer);
    let answer = 43;
  }

Uncaught ReferenceError: 
  answer is not defined at 
  hello (<anonymous>:2:17)
  at <anonymous>:1:1
```

