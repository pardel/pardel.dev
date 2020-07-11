# File Structure

Tests are stored in the **spec** folder.

**Features** are stored in **spec/features**. Eg: spec/features/creating\_projects\_spec.rb

```ruby
require 'spec_helper'
describe 'Creating Projects' do
    it "can create a project" do
         ...
    end
end
describe 'Editing Projects' do
    it "can edit a project" do
         ...
    end
end
```

Behaviour tests are stored in spec/models and there is usually a 1-to-1 relationship with the models:

```ruby
require 'spec_helper'
describe 'A new user' do
    it "should have an email address" do
         ...
    end
end
```

## Setup

### Describe

```ruby
describe()
```

Takes an arbitrary number of arguments:

* 1st is either a reference to a class or module or a string
* 2nd argument \(optional\) must be a string.

Describes can be wrapped in modules to make it more readable:

```ruby
require 'spec_helper'
module Authentication
    describe 'A new user' do
        it "should have an email address" do
             ...
        end
    end
end
```

#### Nesting examples

We can use describe within describes. Also ‘context’ keyword can be used instead of describe for inner ones:

```ruby
describe 'A new user' do
   it "should have an email address" do
     ...
   end
  context "when validated" do
    it "..." do
       ...
    end
  end
end
```

#### Pending

```ruby
pending "to do"
```

or an it\(\) with no block

```ruby
it "should have an email address"
```

### Context

**Alias for describe** - does exactly the same thing. Used to:

* encompass tests that have a common starting "context" in which hooks are used.   There are a nice way to group "similar" tests.
* create a new scope \(similar to describe\) that highlights  the different set of data and actions will be used.

```ruby
describe 'A new user' do

    context "when new" do
        before(:each) do
                    @user = User.new
            end

            it "should have an email address" do
                   ...
            end
    end
end
```

## Initial data

```ruby
describe 'Registration' do

  let!(:user) { FactoryGirl.create(:user) }
  let!(:invite_code) { InviteCode.create(code: ‘test1’, user: user} }
  it "does something" do      ...   end
end
```

Allows one to specify local vars that are created and made available before the test starts. For the example above the vars are: **user**, **invite\_code**.

These local variables can be used within other examples \(see invite\_code above\).

The local variables are available within all the tests in the current describe block as well as the sub describe blocks.

## Specify

```ruby
describe "A new chess board" do
    before(:each) { @board = Chess::Board.new }
    specify { @board.should have(32).pieces }
end
```

This example uses the specify\(\) method instead of it\(\) because specify is more readable when there is no docstring. Both it\(\) and specify\(\) are actually aliases of the example\(\) method, which creates an example.

#### Subjectivity

```ruby
describe Person do
    subject { Person.new(:birthdate => 19.years.ago) }
    specify { subject.should be_eligible_to_vote }
end
```

The subject of an example is the object being described.

Once a subject is declared, the example will delegate should\(\) and should\_not\(\) to that subject, allowing you to clean that up even more:

```ruby
describe Person do
    subject { Person.new(:birthdate => 19.years.ago) }
    it { should be_eligible_to_vote }
end
```

#### Implicit Subject

```ruby
describe User do
    it ‘should be happy’ do
      subject.should be_happy
    end
end
```

or

```ruby
describe User do
    it { should be_happy }
end
```

The subject\(\) method used internally by the example returns a new instance of RSpecUser. Of course, this works only when all the pieces fit. The describe\(\) method has to receive a class that can be instantiated safely without any arguments to new\(\), and the resulting instance has to be in the correct state.

```ruby
subject = User.new
```

Only if the describe block has a class in it.

#### its

```ruby
describe User do
    its(:name) { should eq ‘John’}
end
```

equivalent to

```ruby
describe User do
    it { subject.name.should eq ‘John’ }
end
```

#### Specifying the subject

```ruby
describe User do
    subject { User.new(name: ‘John Smith’) }
    it { subject.name.should eq ‘John’ }
end
```

The subject can be specified.

When dealing with multiple subjects use let:

```ruby
context ‘with a job’ do
  subject { User.new(name: ‘John Smith’) }
  let(:job_dev) { Job.new(name: ‘developer’) }

  its(:job) { should eq job_dev}
end
```

Subject can be aliased to make it clear with one it is:

```ruby
context ‘with a job’ do
  subject(:developer) { User.new(name: ‘John Smith’) }
  let(:job_dev) { Job.new(name: ‘developer’) }

  its(:job) { should eq job_dev}
  developer.job should eq job_dev
end
```

the tests are equivalent

Subjects are created using lazy evaluation - not created until first used.

**let!** - will create before each example!

## Hooks

Before

```ruby
before(:each)
before(:all)
```

After

```ruby
after(:each)
after(:all)
```

Around

```ruby
around(:each)
```

Hooks works for each test even those in inner contexts.

```ruby
require 'spec_helper'
    describe 'A new user' do
        context "when new" do
            before(:each) do
                 @user = User.new
            end
            it "should have an email address" do
                 ...
            end
            end
    end
end
```

