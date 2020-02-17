# window object

**alert**, **prompt** and **confirm** are all window methods.   
**console** is also a property of window.

## Alert

```javascript
alert("Hello World");
```

same as:

```javascript
window.alert("Hello World");
```

## Prompt

```javascript
const input = prompt();
alert(input);
```

same as:

```javascript
const input = window.prompt();
window.alert(input);
```

## Confirm

```javascript
if ( confirm('Are you sure?') ) {
  console.log("Yes");
} else {
  console.log("Nope");
}

alert(input);
```

same as:

```javascript
if ( window.confirm('Are you sure?') ) {
  window.console.log("Yes");
} else {
  window.console.log("Nope");
}

alert(input);
```

## Dimensions

```javascript
‣ window.outerHeight
  1371
‣ window.innerHeight
  1292
‣ window.outerWidth
  1995
‣ window.innerWidth
  1334
```

## Position

```javascript
‣ window.scrollX
  0
‣ window.scrollY
  212
```

## Web page location

```javascript
‣ window.location.hostname
  "127.0.0.1"
‣ window.location.protocol
  "http:"
‣ window.location.port
  "5000"
‣ window.location.host
  "127.0.0.1:5000"
‣ window.location.href
  "https://127.0.0.1:5000/a/DOM/window?test=abc"
‣ window.location.pathname
  "/a/DOM/window"
‣ window.location.search
  "?test=abc"
‣ window.location.origin // NB: Firefox & Chrome only
  "http://127.0.0.1:5000"
```

### **Operations:**

Redirect:

```javascript
‣ window.location.href = "http://www.google.com"
```

Reload:

```javascript
‣ window.location.reload();
```

## History

```javascript
‣ window.history.length
  48
```

Go to previous:

```javascript
‣ window.history.go(-1)
```

## Navigator \(the browser\)

```javascript
‣ window.navigator.appCodeName
  "Mozilla"

‣ window.navigator.appName
  "Netscape"

‣ window.navigator.appVersion
  "5.0 (Macintosh)"

‣ window.navigator.oscpu
  "Intel Mac OS X 10.14"

‣ window.navigator.platform
  "MacIntel"

‣ window.navigator.userAgent
  "Mozilla/5.0 (Macintosh; 
  Intel Mac OS X 10.14; rv:66.0)
  Gecko/20100101 Firefox/66.0"

‣ window.navigator.language
  "en-GB"

‣ window.navigator.cookieEnabled
  true

‣ window.navigator.maxTouchPoints
  0

‣ window.navigator.onLine
  true
```

