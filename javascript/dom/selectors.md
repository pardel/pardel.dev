# selectors

**document** methods that allow us to select elements of from the DOM.

## Single element selectors

Return one element:

```javascript
document.getElementById("el-id")
```

More powerful:

```javascript
document.querySelector("#el-id")
document.querySelector(".el-class")
document.querySelector("ul li")
document.querySelector("li")
  // by default, only returns the first found element
document.querySelector("li:first-child")
document.querySelector("li:last-child")
document.querySelector("li:nth-child(3)")
document.querySelector("li:nth-child(odd)")
document.querySelector("li:nth-child(even)")
  // only the first odd/event gets selected
```

## Multiple element selectors

Return a collection of elements:

```javascript
document.getElementsByClassName("nav-link")
  HTMLCollection(4) [a.nav-link, ...]

document.getElementsByClassName("nav-link")[0]
  <a class="nav-link" href="/">Home</a>

document.getElementsByTagName("li")
  HTMLCollection(7) [li.nav-item, li.nav-item, 
    li.nav-item, li.nav-item, li.breadcrumb-item, 
    li.breadcrumb-item, li.breadcrumb-item.active]

document.querySelectorAll("li.nav-item")
  NodeList(4) [li.nav-item, ...]

document.querySelectorAll("li.nav-item:nth-child(odd)")
  NodeList(2) [li.nav-item, ...]
```

## Multiple element selectors - Conversion to arrays

HTMLCollection can be converted to arrays for easier use. NodeList can't.

```javascript
let navLinks = document.getElementsByClassName("nav-link")
  HTMLCollection(4) [a.nav-link, a.nav-link, a.nav-link, a.nav-link]

navLinks = Array.from(navLinks)
  (4) [a.nav-link, a.nav-link, a.nav-link, a.nav-link]

navLinks.forEach(function(link) {
  ...
})
```

## Chaining selectors

Return one element:

```javascript
document.querySelector("ul.navbar-nav:last-child").getElementsByClassName("nav-link")
  HTMLCollection(4) [a.nav-link, a.nav-link, a.nav-link, a.nav-link]
document.querySelectorAll("ul.navbar-nav li:nth-child(odd)")
  NodeList(2) [li.nav-item, ...]
```



