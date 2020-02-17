---
description: How to make the most of the console
---

# using the console

### Output to console

```javascript
‣ console.log("test")
 test
```

### Output an object

```javascript
‣ console.dir(document.body)
  ▾ body
    aLink: ""
    accessKey: ""
    ...
```

### Output an object using table

```text
‣ console.table({a:1,b:2})
    ---------------------
    | (index)  | Value  |
    ---------------------
    | a        | 1      |
    | b        | 2      |
    --------------------- 
```

### Output a variable using template literals \[ES6\]

```javascript
‣ let width = 100;
‣ console.log(`width is: ${width}`)
  width is: 100
```

### Log errors & warnings

```javascript
‣ console.error("Computer says no")
  ▾ Computer says no

‣ console.warning("Computer says maybe")
  ▾ Computer says maybe
```

### Clear console:

```javascript
‣ console.clear
```

### Execution time

Measure how long some code execution took:

```javascript
‣ console.time('id1')
   ...
‣ console.timeEnd('id1');
   default: 6202.5400390625ms
```

