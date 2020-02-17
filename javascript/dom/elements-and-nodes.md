# elements & nodes

## Relationships between elements/nodes

Elements have children and childNodes but nodes only have childNodes.

### Children

```javascript
const navBar = document.querySelector("ul.navbar-nav")

navBar.childNodes
  NodeList(9) [text, li.nav-item, text, li.nav-item, text, li.nav-item, 
    text, li.nav-item, text]

navBar.children
  HTMLCollection(4) [li.nav-item, li.nav-item, li.nav-item, li.nav-item]

navBar.firstChild
  #text

navBar.firstElementChild
  <li class="nav-item">...</li>

navBar.lastChild
navBar.lastElementChild
```

### Parents

```javascript
const navItem = document.querySelector("ul.navbar-nav").firstElementChild

navItem.parentNode
  <ul class="navbar-nav">...</ul>

navItem.parentElement
  <ul class="navbar-nav">...</ul>

navItem.parentElement.parentElement
  <div class="collapse navbar-collapse">...</div>
```

### Siblings

```javascript
const navItem = document.querySelector("ul.navbar-nav").firstElementChild

navItem.nextSibling
  #text

navItem.nextElementSibling
  <li class="nav-item">...</li>

navItem.previousSibling
navItem.previousElementSibling
```

## Elements

### Properties

```javascript
const element = document.getElementById("el-id")

element.id
  "el-id"

element.style.background = "#ccc"
element.style.color = "#000"
element.style.display = "none"
element.textContent = "New Content"
element.innerText = "New Inner Content"
element.innerHTML = "<strong>New Inner</strong> Content"
```

### Classes

```javascript
const element = document.getElementById("el-id")

element.className
  "el-class el"

element.classList
  DOMTokenList(2) ["el-class", "el", value: "el-class el"]

element.classList.remove("el")

element.classList
  DOMTokenList(2) ["el-class", value: "el-class"]

element.classList.add("test")

element.classList
  DOMTokenList(2) ["el-class", "test", value: "el-class test"]
```

### Attributes

```javascript
const element = document.getElementById("sitemap")

element.hasAttribute("href")
  true

element.getAttribute("href")
  "sitemap"

element.setAttribute("title", "Sitemap")

element.removeAttribute("title")
```

### Create

```javascript
const navBar = document.querySelector("ul.navbar-nav")
const li = document.createElement("li")
li.className = "nav-item"
li.id = "new-nav-item"
li.setAttribute("title", "New Item")
li.textContent = "New nav item"
navBar.appendChild(li)
```

## Replace

```javascript
const navBar = document.querySelector("ul.navbar-nav")
const newNavItem = document.createElement("li")
newNavItem.className = "nav-item"
newNavItem.textContent = "New nav item"
const existingNavItem = navBar.firstElementChild
navBar.replaceChild(newNavItem, existingNavItem)
```

### Remove

```javascript
const navBar = document.querySelector("ul.navbar-nav")
navBar.children[2].remove();
const navItem = navBar.firstElementChild
navBar.removeChild(navItem);
```

## Nodes

```javascript
let navBar = document.querySelector("ul.navbar-nav")
let node = navBar.childNodes[0]

node.nodeName
  "#text"

node.nodeType
  3
```

A list of nodeType constants [available here](https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType).

