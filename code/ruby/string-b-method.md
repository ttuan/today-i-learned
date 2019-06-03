# b - A hidden method in Ruby String

In irb console, I have this code:

```ruby
class Abc
  attr_accessor :a, :b

  def self.new(a, b)
    @a = a
    @b = b
  end
end

o = Abc.new("a", "b")

o.a  # => raise error Nomethod
o.b  # => return string "b"
```

Why? why `o.a` raise error but `o.b` return string `b`????

------

Let's see `new` method. We add `@b = b`, so this method returns `b`. So `o =
Abc.new("a", "b")` => `o = "b"`. And `o.b` ~= `String "b".b`

So I find [here](https://ruby-doc.org/core-2.4.0/String.html#method-i-b)
documment for `b` method :v

Ruby support a method to returns a copied string whose encoding is ASCII-8BIT.

```ruby
>> checkmark = "\u2713"
=> "✓"
>> checkmark.b
=> "\xE2\x9C\x93"
>>
```
So, no magic here, It is just plain Ruby and we just found a mysterious method `String#b`


