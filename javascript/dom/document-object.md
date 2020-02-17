# document object

Is a **window** property

```javascript
‣ window.document
```

same as

```text
‣ document
```

## Document location

```javascript
‣ document.domain
  "127.0.0.1"
‣ document.URL
  "http://127.0.0.1:5000/a/DOM/general?test=abc"
‣ document.contentType
  "text/html"
‣ document.characterSet
  "UTF-8"
```

## Document elements

```javascript
‣ document.all
  HTMLAllCollection(91) [html, head, meta, meta, meta, meta, 
    link, link, link, link, ...]
‣ document.all.length
  92
‣ document.all[2]
  <meta charset="utf-8">
‣ document.doctype
  <!doctype html>
‣ document.head
  <head>...</head>
‣ document.body
  <body>...</body>
```

## Document elements by type

```javascript
‣ document.forms
  HTMLAllCollection []
  
‣ document.forms[0].id
  "1"
  
‣ document.links
  HTMLCollection(9) [a.navbar-brand, a.nav-link, a.nav-link, a.nav-link,
    a, a, a, a.text-muted]
    
‣ document.links[0].className
  "navbar-brand"

‣ document.links[0].classList[0]
  "navbar-brand"

‣ document.images
  HTMLAllCollection []

‣ document.scripts
  HTMLAllCollection(10) [script, ...]

‣ document.scripts[0].getAttribute('src')
  "/assets/rails..."
```

