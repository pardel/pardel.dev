---
description: 'Where to place the JavaScript code:'
---

# script tag

## HTML header

```markup
<html>
  <head>
    <title>Webpage</title>
    <script type="text/javascript">
      console.log("here");
    </script>
  </head>
  <body></body>
</html>
```

```markup
<html>
  <head>
    <title>Webpage</title>
  </head>
  <body>
    <script type="text/javascript">
      console.log("here");
    </script>
  </body>
</html>
```

## External File

app.js

```text
  ...
```

index.html

```markup
<html>
  <head>
    <title>Webpage</title>
    <script src="app.js"></script>
  </head>
  <body></body>
</html>
```

## ES6 - import & export

my-script.js

```javascript
export function House() { 
  this.width = 100;
  this.length = 200;
}
```

second-script.js

```javascript
function paint() { 
  ...
}
function clean() { 
  ...
}
export { paint, clean }
```

index.html

```markup
<html>
  <head>
    <title>Webpage</title>
    <script type="module">
      import { House } from "./my-script.js";
      import { paint, clean } from "./second-script.js";
      let house = new House();
    </script>
  </head>
  <body></body>
</html>
```



## ES10 - dynamic import with async

Early days Google Chrome only

**my-script.js**

```javascript
export const helloEvent = () => {
  console.log('Hello World');
};
```

**index.html**

```markup
<html>
  <head>
    <title>Webpage</title>
    <script type="text/javascript">
      window.onload = function() {
        document.getElementById('helloButton').addEventListener("click", async() => {
          const module = await import('./myscript.js');
          module.helloEvent();
        });
      }
    </script>
  </head>
  <body></body>
</html>
```

