# Stubs & Mocks

**Stub** - replacement for a method with code that returns a specific result

**Mock** - a stub with expectations around it

## Method stubbing

A method stub is a way to overwrite a method by providing a predefined response. It is a generic placeholder for a single method on a single object.

Syntax:

```ruby
allow(my_object).to receive(:my_method).and_return(my_data)
```

So, to stub a method called get on a client object:

```ruby
client.get # returns an xml
```

We'll do this \(xml is a var containing the expected result\):

```ruby
allow(client).to receive(:get).and_return(xml)
```

This way, we get data from a local resource rather than relying on a network resource.

**DANGER**: Stubbing doesn't enforce any rules and it doesn't complain if it never called or called too much.

## Mocking

It enforces rules around stubbing.

```ruby
expect(my_object).to receive(:my_method).and_return(my_data)
expect(client).to receive(:get).and_return(xml)
```

### Test double

A test double is an object that stands in for a real object in an example.

```ruby
user = double('user')
user = stub('user')
user = mock('user')
```

## Message Expectation

A message expectation, aka mock expectation, is a method stub that will raise an error if it is never called.

```ruby
user = double('user')
user.should_receive(:name).and_return('Paul')
```

All together now :\)

```ruby
describe User do
  it "logs a message on new project" do
    user = stub('user')
    user.stub(:name).and_return('Paul')
    logger = mock('logger')
    project = Project(user, logger)
    logger.should_receive(:log).with(/New project for Paul/)
    project.create
  end
end
```

## Test-specific extensions

### Partial stubbing

```ruby
describe WidgetsController do
  describe "PUT update with valid attributes"
    it "redirects to the list of widgets"
      widget = Widget.new()
      Widget.stub(:find).and_return(widget)
      widget.stub(:update_attributes).and_return(true)
      put :update, :id => 37
      response.should redirect_to(widgets_path)
    end
  end
end
```

### Partial mocking

```ruby
describe WidgetsController do
  describe "PUT update with valid attributes"

    it "finds the widget"
      widget = Widget.new()
      widget.stub(:update_attributes).and_return(true)
      Widget.should_receive(:find).with("37").and_return(widget)
      put :update, :id => 37
    end

    it "updates the widget's attributes" do
      widget = Widget.new()
      Widget.stub(:find).and_return(widget)
      widget.should_receive(:update_attributes).and_return(true)
      put :update, :id => 37
    end

  end
end
```

