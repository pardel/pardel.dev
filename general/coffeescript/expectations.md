# Expectations

## be\_valid

```ruby
user = User.new(email: "test@example.org")
 user.save!
expect(user).to    be_valid
```

## shoulda-matchers

```ruby
describe "attributes" do 
  it {
    expect(user).to validate_presence_of :title
  }
 end
```

## allow\_mass\_assignment\_of

```ruby
it { should allow_mass_assignment_of(:title) }
```

## allow\_value

```ruby
it { should allow_value('http://foo.com', 'http://bar.com/baz').for(:website_url) }
it { should_not allow_value('asdfjkl').for(:website_url) }
```

## ensure\_inclusion\_of

```ruby
it { should ensure_inclusion_of(:state).in_range(1..5) }
it { should ensure_exclusion_of(:floors).in_range(5..8) }
```

## ensure\_length\_of

```ruby
it { should ensure_length_of(:bio).is_at_least(15) }
it { should ensure_length_of(:superhero).is_equal_to(6) }
it { should ensure_length_of(:status_update).is_at_most(140) }
it { should ensure_length_of(:password).is_at_least(5).is_at_most(30) }
```

## have\_secure\_password

```ruby
it { should have_secure_password }
```

## validate\_acceptance\_of

```ruby
it { should validate_acceptance_of(:eula) }
```

## validate\_confirmation\_of

```ruby
it { should validate_confirmation_of(:email) }
```

## validate\_presence\_of

```ruby
it { should validate_presence_of(:legs).with_message('Robot has no legs') }
```

## validate\_numericality\_of

```ruby
it { should validate_numericality_of(:gpa) } it { should validate_numericality_of(:age).only_integer } it { should validate_numericality_of(:legal_age).is_greater_than(21) } it { should validate_numericality_of(:height).is_greater_than_or_equal_to(55) } it { should validate_numericality_of(:weight).is_equal_to(150) } it { should validate_numericality_of(:number_of_cars).is_less_than(2) } it { should validate_numericality_of(:birth_year).is_less_than_or_equal_to(1987) } it { should validate_numericality_of(:birth_day).odd } it { should validate_numericality_of(:birth_month).even }
```

## validate\_uniqueness\_of

```ruby
  it { should validate_uniqueness_of(:permalink) }
  it { should validate_uniqueness_of(:slug).scoped_to(:journal_id) }
  it { should validate_uniqueness_of(:key).case_insensitive }
  it { should validate_uniqueness_of(:author_id).allow_nil }
```

[https://github.com/thoughtbot/shoulda-matchers](https://github.com/thoughtbot/shoulda-matchers)

expect\(Bacon.new.edible?\).to be\_true expect\(bacon\).to\_not be\_edible

