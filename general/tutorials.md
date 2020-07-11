# Tutorials

## CodeSchool RubyBits 1

1. Expressions
2. Methods and Classes
3. Classes
4. Active Support
5. Modules
6. Blocks

### 1 Expressions

#### if negative to unless

```ruby
if !x        =>         unless x
  ...                     ...
end                     end
```

#### nil is treated as false

"", 0 & \[\] are all true

#### inline _if_ & _unless_

```ruby
fail "Password is too short" if password.length < 8
fail "No user name set" unless username
```

#### short-circuit OR

```ruby
tweets = timeline.tweets || []
if x || y    #   y is not evaluated is x is not null
x ||= 2
```

#### case statement

Like all the other statements is also returns a value.

### 2 Methods and Classes

#### Optional Arguments \(hash arguments\)

```ruby
def tweet(message, options = {})
  ...
end
```

#### Ruby 1.9 hash syntax

```ruby
tweet("Practising Ruby-Fu!",
  lat: 28.55,
  lng: -81.33,
  reply_id: 223231
)
```

#### Exceptions

```ruby
raise ExceptionClass.new

begin
  ...
rescue
  ...
end
```

#### Splat arguments \(we're sending in an array\)

```ruby
def mention(status, *names)
  ...
end
```

#### Classes

One can pass arguments when using ClassName.new - they are passed onto the initialization method:

```ruby
def initialize
  ...
end
```

#### Accesors

```ruby
attr_accessor :foo
attr_reader :bar
```

#### Class description

```ruby
def to_s
  ...
end
```

#### Reopen classes

```ruby
class ClassName
  ... additional functionality
end
```

### 1.3 Classes

#### Encapsulation

A class is made of state \(data\) & behaviour.

#### Visibility

* methods public by default - public, private, protected
* private methods - cannot be called with explicit receiver
* protected methods - hidden from outside but accessible from other instances of the same class

#### Inheritance

Can only inherit from one class:

```ruby
class Image < Attachment
  ...
end
```

#### Super

super\(\) - method of the same name in the parent class

super with no arguments will automatically use the right arguments

### iVars

Private by default - they are exposed through accessors.

### 1.4 Active Support

Install

```bash
gem install activesupport
gem install i18n            # not required but brings in                                                       lots of goodies
```

#### Addition to Array

```ruby
array.from(4)
array.to(2)
array.in_groups_of(3)
array.split(2)
```

#### Additions to Date

```ruby
aDate.at_beginning_of_day
aDate.at_beginning_of_month
aDate.at_beginning_of_year
aDate.advance(years:4, months: 3, weeks: 2, days: 1)
aDate.tomorrow
aDate.yesterday
```

#### Additions to Hash

```ruby
hash1.diff(hash2)
hash1.stringify_keys
options.reverse_merge(defaults)
new_options.except(:password)
new_options.assert_valid_keys(:user, :lang)
```

#### Additions to Integer

```ruby
index.odd?
index.even?
```

#### Inflections

```ruby
1.ordinalize
"user".pluralize
"women".singularize
"string".titleize
"account_options".humanize
```

### 1.5 Modules

#### Namespaces

By default, functions are created in the global namespace.

#### Module create

```ruby
module ModuleName
  def method1
    ...
  end
end

class Class1
  include ModuleName
end
```

#### Ancestors

```ruby
ClassName.ancestors          -> includes the superclasses
                                and modules
ClassName.included_modules  -> list of included modules
```

#### Mixin

```ruby
extend ModuleName          - expose methods as class methods
include ModuleName         - expose methods as instance methods
object.extend(ModuleName) - expose methods only to that instance
```

#### Hooks - self.included

```ruby
module ModuleName
  def self.included(base)
    ...
  end
end
```

#### Hooks - ActiveSupport concern

Similar in functionality with the self.include hook.

```ruby
require 'active_support/concern'
included do
  ...
end
```

### 1.6 Blocks

#### Array

```ruby
array1.each { |word| puts word }
```

or

```ruby
array1.each do |word|
  puts word
end
```

each is part of the Enumerable mixin.

#### YIELD

```ruby
def call_this_block_twice
  yield
  yield
end
call_this_block_twice { puts "tweet" }   
                                    => tweet tweet
```

#### YIELD with arguments

```ruby
def call_this_block
  yield "tweet"
end
call_this_block { |myarg| puts myarg }
                                        => tweet
call_this_block { |myarg| puts myarg.upcase }   
                                        => TWEET
```

#### YIELD return value

```ruby
def puts_this_block
  puts yield
end
puts_this_block { "tweet" }      => tweet
```

#### USING Blocks

```ruby
class Timeline
  def each
    @user.friends.each do |friend|
      friend.tweets.each do |tweet|
        yield tweet
      end
    end
  end
end

timeline = Timeline.new(user)
timeline.each { |tweet| puts tweet }
timeline.each { |tweet| tweet.cache }
```

#### Enumerable Mixin

```ruby
include Enumerable  <- gives access to lots of methods
```

## Section 2 - CodeSchool’s Ruby Bits 2

### 1. Blocks, procs & lambdas

#### Procs

Objects that can be executed.

```ruby
my_proc = Proc.new { puts “tweet” }
my_proc.call
```

or

```ruby
my_proc = Proc.new do
    puts “tweet”
end
my_proc.call
```

#### Proc to Block

```ruby
block = &proc
```

#### lambda keyword

Very similar with Proc.

```ruby
my_proc = lambda { puts “tweet” }
my_proc.call
```

Since 1.9 - stuby lambdas:

```ruby
my_proc = -> { puts “tweet” }
my_proc.call
```

#### Blocks to Lambdas

```ruby
class Tweet
  def post (success, error)
    ...
    success.call
    ...
    error.call
  end
end

tweet = Tweet.new(‘Ruby Bits!’)
success = -> { puts “Sent!” }
success = -> { puts “Sent!” }
tweet.post(success, error)
```

