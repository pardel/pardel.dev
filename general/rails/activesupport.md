# ActiveSupport

## 1. RESTful routing

config/routes.rb:

```ruby
MyApp::Application.routes.draw do
  resources :users
end
```

| Actions |  | Path | Route |  |
| :--- | :--- | :--- | :--- | :--- |
| index | GET | /users | users\_\[path | url\] |
| show | GET | /users/:id | user |  |
| new | GET | /users/new | new\_user |  |
| create | POST | /users |  |  |
| edit | GET | /users/:id/edit | edit\_user |  |
| update | PUT | /users/:id |  |  |
| destroy | DESTROY | /users/:id |  |  |

e.g.:

```ruby
user_path(@user)
```

### **1.1 Restricting routes**

```ruby
MyApp::Application.routes.draw do
  resources :users, only: [:index, :show]
  resources :groups, except: [:destroy, :edit, :update]
end
```

And to remove duplication across multiple resources, we can use:

```ruby
MyApp::Application.routes.draw do
  with_options only: [:index, :show] do |listing_only|    listing_only.resources :users    listing_only.resources :products  end
end
```

### **1.2. Subdomain constraint**

```ruby
MyApp::Application.routes.draw do
  resources :cms_users, constraint: { subdomain: ‘cms’ }
end
```

or, to avoid duplication across multiple resources:

```ruby
MyApp::Application.routes.draw do
  constraints subdomain: ‘cms’ do    resources :cms_users  end
end
```

### **1.3 Namespaces**

```ruby
MyApp::Application.routes.draw do
  namespace :cms do    resources :cms_users  end
end
```

Routes will now have a cms prefix: cms/cms\_users\#index

In this case, the controller will need to go under a Cms module and the file in a cms folder.

```ruby
SurvivingRails::Application.routes.draw do
  resources :announcements
  namespace :api, path: '/', constraints: { subdomain: 'api' } do    resources :zombies    resources :humans  end  
end
```

### **1.4 Defaults**

```ruby
MyApp::Application.routes.draw do
    scope module: :api, defaults: { format: 'json' } do
    namespace :v1 do        ## resources will be here    end
  end
end
```

## 2. Inflections

### **2.1 Acronyms**

This is used to avoid the camelcase convention on naming \(eg. for classes\).

```ruby
config/initializers/inflections.rb
ActiveSupport::Inflector.inflections(:en) do |inflect|
  inflect.acronym ‘API’
end
```

We can now have an API module and this won’t translate to a\_p\_i in the folder name but to api.

