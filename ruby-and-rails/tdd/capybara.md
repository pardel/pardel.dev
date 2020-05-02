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



