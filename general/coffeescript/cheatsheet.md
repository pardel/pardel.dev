# Cheatsheet

[https://gist.github.com/byplayer/965857](https://gist.github.com/byplayer/965857)

```ruby
module UserSpecHelper
  def valid_user_attributes
    { :email => "joe@bloggs.com",
      :username => "joebloggs",
      :password => "abcdefg"}
  end
end


describe "A User (in general)" do
  include UserSpecHelper

  before(:each) do
    @user = User.new
  end

  it "should be invalid without a username" do
    pending "some other thing we depend on"
    @user.attributes = valid_user_attributes.except(:username)
    @user.should_not be_valid
    @user.should have(1).error_on(:username)
    @user.errors.on(:username).should == "is required"
    @user.username = "someusername"
    @user.should be_valid
  end
end

EXPECTATIONS
=====================
target.should satisfy {|arg| ...}
target.should_not satisfy {|arg| ...}

target.should equal <value>
target.should not_equal <value>

target.should be_close <value>, <tolerance>
target.should_not be_close <value>, <tolerance>

target.should be <value>
target.should_not be <value>

target.should predicate [optional args]
target.should be_predicate [optional args]
target.should_not predicate [optional args]
target.should_not be_predicate [optional args]

target.should be < 6
target.should == 5
target.should be_between(1, 10)
target.should_not == 'Samantha'

target.should match <regex>
target.should_not match <regex>

target.should be_an_instance_of <class>
target.should_not be_an_instance_of <class>

target.should be_a_kind_of <class>
target.should_not be_a_kind_of <class>

target.should respond_to <symbol>
target.should_not respond_to <symbol>

lambda {a_call}.should raise_error
lambda {a_call}.should raise_error(<exception> [, message])
lambda {a_call}.should_not raise_error
lambda {a_call}.should_not raise_error(<exception> [, message])

proc.should throw <symbol>
proc.should_not throw <symbol>

target.should include <object>
target.should_not include <object>

target.should have(<number>).things
target.should have_at_least(<number>).things
target.should have_at_most(<number>).things

target.should have(<number>).errors_on(:field)

expect { thing.approve! }.to change(thing, :status).
    from(Status::AWAITING_APPROVAL).
    to(Status::APPROVED)

expect { thing.destroy }.to change(Thing, :count).by(-1)

Mocks and Stubs
===============
user_mock = mock "User"
user_mock.should_receive(:authenticate).with("password").and_return(true)
user_mock.should_receive(:coffee).exactly(3).times.and_return(:americano)
user_mock.should_receive(:coffee).exactly(5).times.and_raise(NotEnoughCoffeeExcep
ion)

people_stub = mock "people"
people_stub.stub!(:each).and_yield(mock_user)
people_stub.stub!(:bad_method).and_raise(RuntimeError)

user_stub = mock_model("User", :id => 23, :username => "pat", :email =>
"pat@example.com")
```

### Examples \(in the real world\)

[http://madhatted.com/2008/7/10/rspec-real-world-testing](http://madhatted.com/2008/7/10/rspec-real-world-testing) presentation: [http://kerryb.github.com/iprug-rspec-presentation/\#31](http://kerryb.github.com/iprug-rspec-presentation/#31)

## Another Cheatsheet

[https://gist.github.com/zhengjia/428105](https://gist.github.com/zhengjia/428105)

```ruby
=Navigating=
    visit('/projects')
    visit(post_comments_path(post))

=Clicking links and buttons=
    click_link('id-of-link')
    click_link('Link Text')
    click_button('Save')
    click('Link Text') # Click either a link or a button
    click('Button Value')

=Interacting with forms=
    fill_in('First Name', :with => 'John')
    fill_in('Password', :with => 'Seekrit')
    fill_in('Description', :with => 'Really Long Text…')
    choose('A Radio Button')
    check('A Checkbox')
    uncheck('A Checkbox')
    attach_file('Image', '/path/to/image.jpg')
    select('Option', :from => 'Select Box')

=scoping=
    within("//li[@id='employee']") do
      fill_in 'Name', :with => 'Jimmy'
    end
    within(:css, "li#employee") do
      fill_in 'Name', :with => 'Jimmy'
    end
    within_fieldset('Employee') do
      fill_in 'Name', :with => 'Jimmy'
    end
    within_table('Employee') do
      fill_in 'Name', :with => 'Jimmy'
    end

=Querying=
    page.has_xpath?('//table/tr')
    page.has_css?('table tr.foo')
    page.has_content?('foo')
    page.should have_xpath('//table/tr')
    page.should have_css('table tr.foo')
    page.should have_content('foo')
    page.should have_no_content('foo')
    find_field('First Name').value
    find_link('Hello').visible?
    find_button('Send').click
    find('//table/tr').click
    locate("//*[@id='overlay'").find("//h1").click
    all('a').each { |a| a[:href] }

=Scripting=
    result = page.evaluate_script('4 + 4');

=Debugging=
    save_and_open_page

=Asynchronous JavaScript=
    click_link('foo')
    click_link('bar')
    page.should have_content('baz')
    page.should_not have_xpath('//a')
    page.should have_no_xpath('//a')

=XPath and CSS=
    within(:css, 'ul li') { ... }
    find(:css, 'ul li').text
    locate(:css, 'input#name').value
    Capybara.default_selector = :css
    within('ul li') { ... }
    find('ul li').text
    locate('input#name').value
```

