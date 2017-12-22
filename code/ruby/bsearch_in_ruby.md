#bsearch in Ruby

When you wanna find some special elements in an array, you can do it easily with
Ruby. Ruby provides enumerables: `select`, `reject`, `find`, ... so you can do
it. But when the dataset is big, the time to find out result can be increases.

Today, I found a faster way. `Array#bsearch` can find a match with only O(log n)
complexity.

```ruby
require 'benchmark'

data = (0..50_000_000)

Benchmark.bm do |x|
  x.report(:find) { data.find {|number| number > 40_000_000 } }
  x.report(:bsearch) { data.bsearch {|number| number > 40_000_000 } }
end

         user       system     total       real
find     3.020000   0.010000   3.030000   (3.028417)
bsearch  0.000000   0.000000   0.000000   (0.000006)
```
