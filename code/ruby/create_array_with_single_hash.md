# Create an Array with a single Hash withoute the curly braces

Each time I want to create an array, which contains 1 array of Hash, I usualy
write:

```ruby
[{ name: 'Taylor', age: 36 }]

```

But we can do this:

```ruby
[name: 'Taylor', age: 36]

```

The result for both of those will be:

```ruby
[{:name=>"Taylor", :age=>36}]
```

