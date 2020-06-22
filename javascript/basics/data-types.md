---
description: A short overview of JavaScript data types.
---

# Data Types

JavaScript is [weakly typed](https://en.wikipedia.org/wiki/Strong_and_weak_typing): variables can hold different data types at different times and type 'checking' is done at runtime.

**NB:** [Typescript](https://www.typescriptlang.org/) is a **typed superset** of JavaScript that compiles to plain JavaScript - it can be used to enforce type safety.

## Primitive Data Types

Stored on stack so fast to access.

| **value type** | **Constructor** | **Literal** | **typeof\(value\)** |
| :--- | :--- | :--- | :--- |
| **undefined** |  | undefined | "undefined" Useful to check of a variable has been defined if \(typeof answer !== "undefined"\) { ... } |
| **null** |  | null | "object" |
| **bool** | Boolean\(1\) | true false | "boolean" |
| **integer** **decimal**, **float** | Number\(42\) Number\(3.14\) | 42 3.14 | "number" |
| **bigint** \[ES10\] | BigInt\(42\) | 42n | "bigint" |
| **string** | String\("hello world"\) | "hello world" | "string" |
| **symbol** \[ES6\] | Symbol\("abc"\) |  | "symbol" |

## Reference Data Types

Variables are accessed by reference - a pointer to where the data is actually located.  
Stored on head memory \(needs to be allocated\) - the pointers to the heap location are stored on the stack.

| value type | Constructor | Literal | typeof\(value\) |
| :--- | :--- | :--- | :--- |
| **array** | Array\(1, "2", true\) | \[1, "2", true\] | "object" To determine if array check for length property or Array.isArray\(varName\). |
| **object** |  |  | "object" |
| **class object** eg. Date |  |  | "object" |
| **function** | Function\(\) |  | "function" |

Classes are a type of function \([https://www.digitalocean.com/community/tutorials/understanding-classes-in-javascript](https://www.digitalocean.com/community/tutorials/understanding-classes-in-javascript)\).

Setting the value for a key in a dictionary doesn't delete that key.

### Objects

Simple container for **name:value** pairs:

```javascript
‣ const person = {
    name:"Paul", 
    location:"London",
    hello() {
      console.log(`Hello ${this.name}`);
    }
  }
  
‣ console.log(person);
  Object { name: "Paul", location: "London", hello: hello() }
  
‣ person.name
  "Paul"
  
‣ person.hello
  function hello()

‣ person.hello()
  Hello Paul
```

### Nested objects

```javascript
‣ const person = {
    name:"Paul", 
    hello() {
      console.log(`Hello from ${this.address.city}!`);
    },
    address: {
      city: "London",
      country: "UK"
    },
  }
  
‣ console.log(person)
  Object { name: "Paul", hello: hello(), address: {…} }
  
‣ person.hello()
  Hello from London!
```

## Type conversions

#### **Using Constructors**

Eg: for string, use String\(expression\).

```javascript
‣ String(42)
  "42"
‣ String(["John", "Paul", "George", "Ringo"])
  "John,Paul,George,Ringo"
```

**Special methods**

Eg: for strings, use \(expression\).toString\(\).

```javascript
‣ (42).toString()
  "42"
‣ (42.1234).toFixed(2)
  "42.12"

‣ (["John", "Paul", "George", "Ringo"]).toString()
  "John,Paul,George,Ringo"

‣ Number("42.3")
  42.3

‣ parseInt("42.3")
  42
‣ parseFloat("42.3")
  42.3
```

Not all values can be converted:

```javascript
‣ Number("test")
  NaN
```

