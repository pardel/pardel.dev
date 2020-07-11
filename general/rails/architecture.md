# Architecture

## 1. MVC

Model View Controller

### **Model**

The model is \[only\] responsible for maintaining the system state ; this can be either temporary \(even one iterations\) or permanent \(and stored in a storage system\).

The model should incorporate **both**:

* the data - the storage system
* the business logic/rules that govern that data; it is responsible for the well being of that data i.e. the data gatekeeper

### **View**

Responsible for generating the user interface.

### **Controller**

Responsible for bringing together all the system parts.

Path for an incoming request:

* router - identifies the controller and action that will do the work
* the controller/action is responsible for making sense of the data sent in \(if any\)
* the controller interacts with the model \(if required\)
* the controller invoked the view code \(passing in the data required by the view\) and send the result to the browser

### MVC in Rails

#### **Model - ActiveRecord**

An Object-Relational Mapping \(ORM\) library maps database tables to classes:

* a table is mapped to a class
  * the column names become the class object attributes
* a record in a table is mapped to an object of the relevant class

The ORM used by Rails is called ActiveRecord - model example:

```ruby
require 'active_record'
class Book < ActiveRecord::Base
  attr_accessible :title

  def purchase
    ...
  end
end
```

The model can now be used:

```ruby
book = Book.find_by_title(“Rails in Action”)
book.purchase
```

**View & Controller - ActiveSupport**

Since the view and controller interact in a very intimate way, Rails provide one library for both: ActiveSupport.

## 2. Install

```text
gem install rails -v 4.0.0
```

### **2.1. Local copy of the Rails docs**

Create a dummy app and generate the docs:

```text
paul@Pro2:~ $ rails new mydocs
paul@Pro2:~ $ cd mydocs/
paul@Pro2:mydocs $ rake doc:rails
```

The docs are now in the doc/api folder - we’ll move them to the Desktop and delete the temporary app:

```text
paul@Pro2:mydocs $ mv doc/api ~/Desktop/RailsApi
paul@Pro2:mydocs $ cd ..
```

### **2.2.Bundle**

Gems go in the Gemfile. To install the new gems:

```text
bundle update
```

\(tells Bundler to ignore your Gemfile.lock and use your Gemfile to install all the gems specified in it\)

```text
bundle install
```

\(uses the Gemfile.lock file so will install the exact versions from there\).

By default, when Rails generates an application, it runs bundle install --binstubs. The --binstubs option stores executable files in the bin directory at the root of your application for the gems that have executables.

## 3. Assets

In the development environment, the app/assets/javascripts/xxx.js.coffee and app/assets/stylesheets/xxx.css.scss files are automatically parsed into Javascript and CSS respectively, and served via a gem that comes with Rails called Sprockets.

