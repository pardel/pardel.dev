# Debugging

## Logging

**The simplest way to debug but very slow to use**

Logging is the simplest way to debug but, unfortunately, it is very slow to use.

There are 5 levels of debugging: _Debug, Info, Error, Warn & Fatal._ Info is used in production whilst Debug is used by default for the other environments. To change it just add the following to the relevant config/environments/environment.rb file:

```ruby
config.log_level = :debug
```

Here is how to log:

```ruby
logger.debug “The value of var1 is #{var1}” logger.debug array1.inspect
```

## view helpers

In Rails, pry and byebug are debuggers installed as gems that can be used to pause execution and inspect the current state of the code. You use them by placing binding.pry or byebug in your code:

```ruby
# app/controllers/users_controller.rb
def show
  user = User.find(1)
  # example pry usage
  binding.pry
end

> user.first_name
# "Dave"
```

## View helpers

Rails provides view helpers that can be used to show the contents of an object on the page. Since the text is inserted into the final HTML output though, it can impact page layout.

```ruby
<%= debug @article %>
<% # shows a YAML representation of article %>
```

