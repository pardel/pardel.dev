# Local & Session Storage

## Local Storage

Stores key:value pairs of strings. **Persists between browser launches**.

```javascript
window.localStorage
localStorage.setItem("name", "John")
localStorage.getItem("name")
localStorage.removeItem("name")
localStorage.clear()
```

## Session Storage

Stores key:value pairs of strings. **Gets cleared once the browser is closed**.

```javascript
window.sessionStorage
sessionStorage.setItem("name", "John")
sessionStorage.getItem("name")
sessionStorage.removeItem("name")
sessionStorage.clear()
```

## Storing Arrays

```javascript
const notes = JSON.parse(localStorage.getItem("notes"))
localStorage.setItem("notes", JSON.stringify(notes))
```

