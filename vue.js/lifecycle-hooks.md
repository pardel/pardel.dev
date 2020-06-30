---
description: 'Callback functions for Vue’s lifecycle phases:'
---

# Lifecycle hooks

[https://vuejs.org/v2/api/\#Options-Lifecycle-Hooks](https://vuejs.org/v2/api/#Options-Lifecycle-Hooks)

```javascript
var app = new Vue({
  el: '#app',
  data: {
    greeting: 'Hello World!' 
  },
  beforeCreate: function() {
    console.log("beforeCreate");
  },
  created: function() {
    console.log("created");
  },
  beforeMount: function() {
    console.log("beforeMount");
  },
  mounted: function() {
    console.log("mounted");
  },
  beforeUpdate: function() {
    console.log("beforeUpdate");
  },
  updated: function() {
    console.log("updated");
  },
  beforeDestroy: function() {
    console.log("beforeDestroy");
  },
  destroyed: function() {
    console.log("destroyed");
  }
});
```

When created, order is:

* beforeCreate
* created
* beforeMount
* mounted

On update \(eg. property updated\):

* beforeUpdate
* updated

On exit:

* beforeDestroy
* destroyed



