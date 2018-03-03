# Lazy Evaluation

Lazy evaluation is an evaluation strategy that delays the assessment of an expression until its value is needed.

Example:

```
power_array = -> (power, array_size) do
    1.upto(Float::INFINITY).lazy.map { |x| x**power }.first(array_size)
end

puts power_array.(2 , 4)    #[1, 4, 9, 16]
puts power_array.(2 , 10)   #[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
puts power_array.(3, 5)     #[1, 8, 27, 64, 125]
```

In this example, lazy avoids needless calculations to compute power_array.
If we remove lazy from the above code, then our code would try to compute all  ranging from  to Float::INFINITY.
To avoid timeouts and memory allocation exceptions, we use lazy. Now, our code will only compute up to first(array_size).
