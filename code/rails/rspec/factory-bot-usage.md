# FactoryBot Usage

1. Alias

```ruby
factory :user, aliases: [:author, :commenter] do
  first_name { "John" }
  last_name { "Doe" }
  date_of_birth { 18.years.ago }
end
```

Co the su dung trong truong hop self join ;)

2. Inheritance

```ruby
factory :post do
  title { "A title" }
end

factory :approved_post, parent: :post do
  approved { true }
end
```

3. Associations

FactoryBot support strategy. we can custom stragety to using our own logic

```ruby
# Build post with different association of user, or just `build`, not create
factory :post do
  # ...
  association :author, factory: :user, last_name: "Writely", strategy: :build
end
```

4. Sequences

```ruby
FactoryBot.define do
  sequence :email do |n|
    "person#{n}@example.com"
  end
end

# Use
factory :user do
  email
end
```

5. Trait

Traits allow you to group attributes together and then apply them to any factory. helps remove duplication

```ruby
FactoryBot.define do
  factory :post do
    title { 'An awesome post' }
    body { 'Lorem Ipsum...' }

    trait :published do
      status { :published }
    end

    trait :unpublished do
      status { :draft }
    end

    trait :with_comments do
      after(:create) do |post|
        create_list :comment, 2, todo_item: post
      end
    end
  end
end

# then in your test

let(:post) { create(:post, :published) }

# or even with

let(:post) { create(:post, :published, :with_comments) }
```

6. Callbacks

```ruby
factory :user do
  after(:build) { |user| generate_hashed_password(user) }
end
```

7. Create multiple records

```ruby
twenty_year_olds = build_list(:user, 25, date_of_birth: 20.years.ago)
stubbed_users = build_stubbed_list(:user, 25) # array of stubbed users
users_attrs = attributes_for_list(:user, 25) # array of attribute hashes
```

8. Linting Factories

```ruby
FactoryBot.lint
```
