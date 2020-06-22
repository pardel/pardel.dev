---
description: >-
  a library that makes it easy to simulate how a user interacts with your
  application.
---

# Capybara

Project page: [http://teamcapybara.github.io/capybara/](http://teamcapybara.github.io/capybara/)

DSL: [https://rubydoc.info/github/teamcapybara/capybara\#the-dsl](https://rubydoc.info/github/teamcapybara/capybara#the-dsl)



### Testing views

```ruby
RSpec.describe "settings/index.html.erb", type: :view do
  it "- renders content" do
    render
    expect(rendered).to have_css('h1', text: 'Settings')
    expect(rendered).to_not have_css('p', text: 'Welcome!')
    expect(rendered).to have_link("Login", href: login_path)
    expect(rendered).to have_no_link("Resend welcome email")
  end
end
```



Using  [ActionController](https://apidock.com/rails/ActionController)::[Assertions](https://apidock.com/rails/ActionController/Assertions)::[SelectorAssertions](https://apidock.com/rails/ActionController/Assertions/SelectorAssertions) :

```ruby
RSpec.describe "settings/index.html.erb", type: :view do

  before :each do 
    @user = FactoryBot.create(:user)
    assign(:user, @user)
    render
  end 
  
  it "- renders content" do
    assert_select 'h1', 'Settings'
    
    # LINKS
    assert_select 'a', {count: 1, text:'Log in', href: login_path}
      # check that not present
    assert_select "a[text=?]", "Resend welcome email", false
    
    # FORMS
    assert_select 'form[action=?][method=?]', settings_update_path, 'post' 
    assert_select 'form input[name=?][id=?][value=?]', 'user[firstname]', 
      'user_firstname', @user.firstname
    assert_select 'form input[name=?][id=?][value=?]', 'user[lastname]', 
      'user_lastname', @user.lastname
    assert_select 'form input[name=?][id=?][value=?][disabled=?]', 
      'user[email]', 'user_email', @user.email, 'true'
    assert_select 'form button[type=?][id=?]', 'submit', 'update'
    
      
  end
  
end
```

Gotchas:

* assign variables before rendering
* when checking if an element with a certain property doesn't exist, these 'obvious' way don't work: `assert_select 'a', { text: "Resend welcome email" }, false`  - presence assertion `assert_select 'a', false, { text: "Resend welcome email" }` - lack of presence assertion but properties ignored
* **Be very specific when you search for presence but vague when checking for lack of presence.** E.g. check if a link with text is missing rather than a link with text and href, like you would do if checking for presence. 



