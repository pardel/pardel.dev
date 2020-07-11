# ActiveRecord

## 1. ActiveRecord::Base

All model classes extend from it:

```ruby
require 'active_record'
class User < ActiveRecord::Base

end
```

## 2. Database

### **2.1 Migrations**

```ruby
class CreateUsers < ActiveRecord::Migration
  def change
    create_table :users do |t|
      ...
    end
  end
end
```

or

```ruby
class CreateUsers < ActiveRecord::Migration
  def up
    create_table :users do |t|
      ...
    end
end
  def down
    drop_table :users
  end
end
```

Run the migrations \(default environment is Development\):

```text
bin/rake db:migrate
and prepare the test database:
bin/rake db:test:prepare
```

## 3. Strong parameters

Specify which parameters are to be accepted when creating a new object. Here is the error when not using them:

```text
Failure/Error: click_button 'Register'
     ActiveModel::ForbiddenAttributesError:
       ActiveModel::ForbiddenAttributesError
```

## 4. Associations

```ruby
class Blog < ActiveRecord::Base
    ...
    has_many comments
end
```

Once can write methods that are run only on collections of comments for a blog. Called: association extensions.

```ruby
class Blog < ActiveRecord::Base
    ...
    has_many comments do
        def refresh        ...        end
    end
end
```

Now we can use:

```ruby
blog.comments.refresh
```

The block has access to a proxy\_association object that has an owner attribute so we can use proxy\_association.owner to refer to the blog.

