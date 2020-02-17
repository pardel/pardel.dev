# Add to an existing Page

#### Step 1: Add Vue.js

We'll include the latest version from the CDN, at the bottom of the page just before the closing **&lt;/body&gt;** tag:

```text
<script src="https://cdn.jsdelivr.net/npm/vue@2.6.0"></script>
```

Let's also create a new js file, named **main.js** and include it just after the one above:

```text
<script src="main.js"></script>
```

#### Step 2: Create the Vue instance

In main.js, let's create our Vue instance:

```javascript
var app = new Vue({
  el: '#app',
  data: {
    welcome: 'Welcome to Vue.js!'
  } 
})
```

**Note:** The html file includes a div with an id of \`app\` - this will be used to "host" the Vue app - this is specified by the \`el\` property of our Vue instance.

The Vue app also provides a simple data property called **welcome**.

#### Testing

We'll add a {{ welcome }} expression in the HTML file - it will be replace by the Vue's data welcome property.

Here is the final content of the HTML file:

```markup
<html>
  <head>
    <title>Basic Vue</title>
  </head>
  <body>
    <div id="app">
      <h1>Vue.js</h1>
      <p>{{ welcome }}</p>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.0"></script>
    <script src="main.js"></script>
  </body>
</html>
```

### Result!

![](https://learn-js-dev.herokuapp.com/images/vue/basics/install.png)

