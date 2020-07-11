# RSpec matchers

... and not assertions.

rspec 1 & 2 - uses xxx.**should**

rsoec 2 - uses **expect**\(xxx\).**to**

#### Should

At the core of RSpec.

```ruby
answer.should equal(42)
second_answer.should_not equal(42)
```

#### Expect\(\).to

```ruby
expect((User.where(email: user.email).first).is_active).to eq(true)
```

## Matchers

```ruby
answer.should equal(42)
people.should include(john)
user.should respond_to(:send_email)
```

### Regular expressions

```ruby
person.name.should **match**(/John/)
```

### Matching numerical values

```ruby
answer.should equal(42)
order.total.should be_close(25.20, 0.01)  #floating point pain
```

### Predicate Matchers

```ruby
answer.should be_empty
```

gets translated to:

```ruby
answer.empty?.should == true
```

or

```ruby
answer.should be_valid
```

gets translated to the Active Record valid? method:

```ruby
answer.valid?.should == true
```

This can be translated for any methods:

```ruby
user.should be_in_list('admin')
user.in_list?('admin').should == true
```

RSpec **strips off the "be\_" and appends "?"; then it sends the resulting message to the given object**. RSpec also looks for things prefixed with "be_a_" and "be_an_".

### Booleans

```ruby
answer.should be_true
answer.should be_false
```

be\_false checks for false and nil For checking the actual boolean true or false:

```ruby
answer.should equal(true)
answer.should equal(false)
```

### Collections

Use the have matcher:

```ruby
answer.should have_key(:id)
```

**have\_** translates to **has\_** method on the object.

```ruby
users.should have(37).items
"this string".should have(11).characters
```

.items and .characters are pure syntactic sugar.

```ruby
day.should have_exactly(24).hours
dozen_bagels.should have_at_least(12).bagels
internet.should have_at_most(2037).killer_social_networking_apps
```

have\_exactly is just an alias for have.

### Operators

```ruby
result.should == 3
result.should =~ /some regexp/
result.should be < 7
result.should be <= 7
result.should be >= 7
result.should be > 7
```

### Raising Errors

```ruby
expect { user.save! }.to raise_error(
  ActiveRecord::RecordInvalid
)
```

or

```ruby
expect { user.save! }.to_not raise_error(
  ActiveRecord::RecordInvalid
)
```

### Change Matcher

```ruby
expect { <code that causes the change> }.to change { <param changed> }.by(<value>
```

### Other matchers

```ruby
be_within(range).of(expected)

satisfy { block }

exist
be_kind_of(class)
be_an_instance_of(class)
respond_to(method_name)
```

### Custom Matcher

```ruby
expect(my_date).to match_date "2013-12-22"
```

match\_date is the custom matcher

Should be defined in a file in spec/support/ folder.

## Capybara

### Actions

```ruby
visit '/'
visit root_url

click_link 'New Project'
click_button 'Create Project'

page.driver.post(registration_do_path, { user: {email: random_email} })
```

### Forms

```ruby
fill_in 'Name', :with => 'TextMate 2' 
fill_in 'project[name]', :with => project_name

select('option', :from => 'select box')
 choose('A radio button')
check('A checkbox')
attach_file('Image', '/path/to/image.jpg')
```

### Scoping

```ruby
within("elementId") do   ... end

within_table('myTable') do   ... end
```

### Mouse actions - Hover

```ruby
page.execute_script('$("#doc_' + document1.id.to_s + '").trigger("mouseenter")')
```

### Expectations - Page status

```ruby
expect(page.status_code).to be(200)
expect(page.current_url).to eq(login_url)
response.should be_success     # especially useful for APIs
```

### Expectations - HTML

**have\_title**

```ruby
expect(page).to          have_title 'Main page'
expect(find("title").native.text).to have_content(title)
```

**have\_content**

```ruby
expect(page).to         have_content 'Project created.'
 expect(page).to_not      have_content 'Make it nice'
```

**have\_css**

```ruby
expect(page).to        have_css 'h1#doesnotexist'
```

**have\_selector**

```ruby
expect(page).to     have_selector 'h1', text: 'Main header'
```

You can be as **specific** as you want with a selector:

```ruby
expect(page).to have_selector 'div#header h1', text: 'Welcome'
expect(page).to have_selector 'li a', text: 'Click here'
```

### Expectation forms

```ruby
page.has_checked_field?('user_gender_').should be_true
page.has_no_checked_field?('user_gender_f').should be_true

find_field('user_height').value.should be_nil
```

### Title

```ruby
string.has_title?('simple_node').should be_true
```

### Matching with text options

```ruby
page.should have_css('h1', :text => 'Totally awesome')
```

### Visibility

```ruby
string.all(:css, '#secret', :visible => true).should be_empty
string.all(:css, '#secret', :visible => false).should have(1).element
string.find(:css, "#secret", :visible => false).should_not be_visible
```

### Xpath

```ruby
page.should have_xpath('//a[@id="doc_delete_2]')
page.find('//h1').text.should == 'Totally awesome'
page.find('//h1')[:data].should == 'fantastic'
page.find('//h1').tag_name.should == 'h1'
page.find('//h1').path.should == '/html/body/div/div[1]/h1'
page.find('//div/input').value.should == 'bar'
page.find('//select').value.should == 'Capybara'
```

### Regex

```ruby
page.has_title?(/s[a-z]+_node/).should be_true
page.has_title?(/monkey/).should be_false
```

continue here: [https://github.com/jnicklas/capybara/tree/master/spec](https://github.com/jnicklas/capybara/tree/master/spec)

### Visualise

```text
gem 'launchy'
```

and then use

```ruby
save_and_open_page
```

... in the test before the method you expect to fail, Capybara will launch the browser with the content of the page or save the screenshot to the temp folder.

