# Curry in Ruby

Returns a curried proc. If the optional arity argument is given, it determines the number of arguments. A curried proc receives some arguments.
If a sufficient number of arguments are supplied, it passes the supplied arguments to the original proc and returns the result.
Otherwise, returns another curried proc that takes the rest of arguments.

For example:

```
multiply_numbers = -> (x,y) do
    x*y
end

doubler = multiply_numbers.curry.(2) # 'double' function has not been called.  just assign x = 2
tripler = multiply_numbers.curry.(3)

puts doubler.(4)    #8 = 2 * 4. Cause it assign y = 4 and multiple it with x = 2 above
puts tripler.(4)    #12
```
