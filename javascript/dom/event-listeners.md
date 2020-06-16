# event listeners

## window.onload

The load event fires when a given resource has loaded - for the window, this is when all dependencies have been loaded.

```markup
    <html>
      <head>
        <title>Webpage</title>
        <script type="text/javascript">
          window.onload = function() {
            ...
          }
        </script>
      </head>
      <body></body>
    </html>
```

## DOMContentLoaded

Listener for when the document has loaded \(but not its dependencies\).

```markup
    <html>
      <head>
        <title>Webpage</title>
        <script type="text/javascript">
          function loaded() {
            console.log("DOM loaded");
          }
          if (document.readyState == "loading") {
            document.addEventListener("DOMContentLoaded", loaded);
          } else {
            loaded();
          }
        </script>
      </head>
      <body></body>
    </html>
```

### Element Event Listeners

```javascript
const el = document.querySelector("#anElement");

el.addEventListener('click', function(event){
  console.log("element clicked");
  e.preventDefault();
})

// or

el.addEventListener('click', onClick);
function onClick(){
  console.log("element clicked");
  e.preventDefault();
}
```

Event types can be [found here](https://developer.mozilla.org/en-US/docs/Web/Events).

For an array of elements:

```javascript
Array.from(document.getElementsByClassName("time_delta")).forEach(function(element) {
    element.addEventListener('click', function(event){
      console.log(event);
    });
  });
```

## Event Properties

```javascript
// The element the event happened on:

event.target
event.type
event.timestamp

// Coordinates

// relative to the window
event.clientX
event.clientY

// relative to element
event.offsetX
event.offsetY
```

## Mouse Events

Used with  **element.addEventListener\('xxx', onClick\)**:

```javascript
click
dblclick
mousedown
mouseup

// Enter and leave the element
mouseenter
mouseleave 

// Over element itself
mouseover

// Over one of its children
mouseout

// Change of position
mousemove
```

## Keyboard & Input Events

Used with  **element.addEventListener\('xxx', onClick\)**:

```javascript
// Forms
submit

// Inputs
keydown
keyup
keypress
focus
blur
cut
paste

// any event on input
el.addEventListener("input", doSomething);

// Select
keydown
```

## Event Bubbling

Events are, by default, bubbling up throughtout the DOM, i.e. an event received by an element will also be received by all ancestors of that element.

## Event Delegation

Technique through which events received by an element are "propagated" to its children. This is particulary useful when the children are created dynamically. This is done by checking the event target \(which is not always the element that received the action.

```javascript
document.body.eventListener("click", someAction);

function someAction(event) {
  if (event.target.classList.contains("something")) {
      console.log("do some action");
      // EG:
      event.target.parentElement.remove();
  }
}
```

