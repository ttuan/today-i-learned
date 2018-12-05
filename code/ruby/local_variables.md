# Local variables in Ruby

In Ruby, everytime we execute 1 function, all local variables in this function will be initialize BEFORE we run code in it.

For example:

```ruby
# irb

def test_func
  binding.pry
  if fasle
    x = 2
  end
end

test_func
```

If you stay at `binding.pry` and call: `local_variables`, you can see variable `x` is defined, with value = nil, dispite the code `x = 2` is not execute.


