# General

* A statements ends with a semicolon or at the end of line.
* Comments start with a \#
* Indentation - 2 spaces is the de facto standard.

[https://rubystyle.guide/](https://rubystyle.guide/)

## Objects everywhere

Everything in Ruby is an object! Objects are created by calling a constructor: the new method of the class.

**nil** is an object.

## Naming conventions

* local vars, method params & method names - start with a lowercase or underscore. Underscores are also used to separate words \(no camelCase\)
* class names, module names & constants - start with an uppercase and use capitalisation rather than underscore \(PascalCase\)
* constants are written in all uppercase with underscores to separate words

## Symbols

Used to identify things - usually to identify the methods params and identify hash contents.

**Format** - colon followed by lowercase and underscore \(similar with var names\). Eg: :action redirect\_to :action =&gt; "edit", :id =&gt; params\[:id\]

## Data types

### Strings

Ordered collections of chars \(bytes\).

**String literal** - sequence of characters enclosed by single or double quotation marks.

When using double quotes, Ruby does the followings:

* substitutions - for special characters \(start with /\) eg: \n
* expression interpolation - replaces the \#{expression} with the expression valuation.

### Numbers

Integer, float

```ruby
10 / 4
 => 2 
10 / 4.0
 => 2.5 
```

Auto-conversation when required. eg ^ 10 converted to float.

```ruby
10.class
 => Integer 
10.0.class
 => Float 
10 == "10"
 => false 
10 == 10.0
 => true 
10.eql?(10.0)
 => false
```

### Collections - Arrays & Hashes

Collections of objects accessible via a key:

* for arrays - the key is an integer
* for hashes - the key myst be unique

Can hold objects of different types - keys in a hash can also be arbitrary objects. Arrays are more efficient for Hashes are more flexible.

**Array literal** - set of elements between square brackets.

```ruby
my_array = [1, 2, nil, 4]
```

Remember: nil is an object!

Shortcut for array of words:

```ruby
%w{ London Rome  Paris }
```

Access using subscripts:

```ruby
my_array[1]
```

**Hash literal** - even set of elements between braces.

```ruby
my_hash = {
  :london => ‘Boris Johnson’,
  :paris => ‘Jean Luc’
}
```

Special syntax from Ruby 1.9:

```ruby
my_hash = {
  london: ‘Boris Johnson’,
  paris: ‘Jean Luc’
}
```

```ruby
my_hash.keys
my_hash.values
```

### Ranges

```ruby
1..10
"a".."z"

(0...10).to_a
 => [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] 
(0..10).to_a
 => [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10] 
```

## Methods

```ruby
def sum(a, b)
  return a + b
end

sum(2, 3)
```

Paranthesis are optional if method doesn't take any arguments.

When passing a hash as argument, the braces are optional

```ruby
rate_book :book => ‘Rails in Action’, :rating => 5
```

value of last statement in a method is returned

```ruby
def sum(a, b)
  c = 2 * a
  c + b
end

sum(2, 3)
 => 12
```

## Regular expressions \(Regex\)

Specifies a pattern to match in a string.

**Regex literal** - /pattern/ or %r{pattern}

**Match operator** - var\_1 =~ /Rail\[s\]/

## Evaluating objects

nil is treated as false "", 0 & \[\] are all true

Include other source files

```ruby
require  “path/to/file”  # the path is absolute to the project
require_relative “../../path/to/file” # relative to the current file
```

## Introspection

Everything is a class:

```ruby
"test".class
 => String 
42.class
 => Integer 
42.methods
 => [:-@, :**, :<=>, ... ] 
"test".is_a?(String)
 => true 
```

## Miscellaneous

### \_

\_ returns the value of the last evaluated expression:

```ruby
a = 2 + 5
 => 7
b = _
 => 7 
```

### Load paths

`$LOAD_PATH` holds paths where files can be `require` 'd from.

```ruby
# file1.rb
require_relative 'file2'
```

Or, adding path to `$LOAD_PATH`:

```ruby
$LOAD_PATH << "."
require 'file2'
```

