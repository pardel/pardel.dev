# Classes

```ruby
class Car
  def initialize(colour)
    @colour = colour
  end
  def to_s
    "#{@colour} car"
  end
end

my_car = Car.new("red")
puts my_car
  => red car
```

Instance variables start with `@` and are private.

### Accessors

```ruby
class Car
  attr_accessor :colour, :brand
  def initialize(colour, brand)
    @colour = colour
    @brand = brand
  end
  def to_s
    "#{@colour} #{@brand}"
  end
end

my_car = Car.new("red", "ford")
puts my_car
  => "red ford"
puts my_car.colour
  => "red"
my_car.colour = "green"
puts my_car
  => "green ford"

```

## Modules



