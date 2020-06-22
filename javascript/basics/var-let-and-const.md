---
description: Exploring the different ways of defining data containers.
---

# var, let, & const

## var

 \(sole way before ES2015/ES6\)

_Legacy_ keyword to add a _**global** variable_. They are declared in the global scope regardless where the actual declaration occurs - this is called variable hoisting in the JavaScript world. These variable are also made available as property to the window object \(the default context\).

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

Introduced in ES2015/ES6. Similar way to define a variable but with scope constraints.

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

Variables cannot be re-declared using `let`, unlike `vars`   \(SyntaxError thrown\):

```javascript
‣ var x = 1;
‣ var x = 2;
‣ let answer = 42;
‣ let answer = 42;
  SyntaxError: redeclaration of let answer
```

## const

Introduced in ES2015/ES6. Creates a constant - once defined, it **cannot be re-assigned a value.**

```javascript
‣ const answer = 42;
‣ answer = 43;
  Uncaught TypeError: 
  Assignment to constant variable.
```

**Also, cannot be declared without a value.**

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

## Best practice

* never use `var`
* start with `const` if unsure if a data container will change value
* move to `let` when required

