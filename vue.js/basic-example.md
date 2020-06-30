# Basic example

Assuming a basic HTML webpage:

```markup
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Basic example</title>
</head>
<body>
  
</body>
</html>
```

## 1. Include Vue.js \(in head\)

```markup
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

## 2. App DOM element

```markup
<div id="app">
  <h1>{{greeting}}</h1>
</div>
```

Or, using element attribute binding:

```markup
<div id="app">
  <h1 v-text="greeting"></h1>
</div>
```

## 3. Create the app \(file app.js\)

```javascript
var app = new Vue({
  el: '#app',
  data: {
    greeting: 'Hello World at ' + new Date().toLocaleString()  + '!'
  }
});
```

and include it in the HTML:

```markup
<script src="app.js"></script>
```

Complete listing:

`basic.html`

```markup
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>
<body>
  <div id="app">
    <h1>{{greeting}}</h1>
  </div>
  <script src="app.js"></script>
</body>
</html>
```

`app.js`:

```javascript
var app = new Vue({
  el: '#app',
  data: {
    greeting: 'Hello World at ' + new Date().toLocaleString()  + '!'
  }
});
```

