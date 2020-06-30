# Cheatsheet

Show/hide divs:

```javascript
document.getElementById('auth-view').style.display = 'none'
document.getElementById('todo-view').style.display = 'block'
```

Form submission / listeners:

```javascript
<div id="auth-view">
  <h1>Login</h1>
  <form id="login-form">
    <input id="login-username" type="text" required placeholder="Username">
    <input id="login-password" type="password" required placeholder="Password">
    <input type="submit" value="Sign in">
  </form>
  <div id="login-error"></div>
</div>
<script type="text/javascript">
function handleLogin(e) {
  e.preventDefault()
  const username = document.getElementById('login-username').value
  const password = document.getElementById('login-password').value

  app.signIn(username, password)
    .then((user) => showTodos(user))
    .catch((e) => document.getElementById('login-error').innerHTML = e)
}

document.getElementById('login-form').addEventListener('submit', handleLogin);
</script>
```

Add Children:

```javascript
const todosList = document.getElementById('todos');

const todoDelete = document.createElement('button')
todoDelete.innerHTML = 'X'
todoDelete.style.display = 'inline-block'
todoDelete.onclick = () => {
  app.deleteItem({ itemId: itemId })
    .catch((e) => document.getElementById('add-todo-error').innerHTML = e)
}

const todoLabel = document.createElement('label')
todoLabel.innerHTML = items[i].item.todo
         
const todoItem = document.createElement('div')
todoItem.appendChild(todoDelete)
todoItem.appendChild(todoLabel)
todosList.appendChild(todoItem)
```





Resources:

* Userbase guide: [https://github.com/encrypted-dev/userbase-samples/blob/master/ugliest-todo/index.html](https://github.com/encrypted-dev/userbase-samples/blob/master/ugliest-todo/index.html)
* 
