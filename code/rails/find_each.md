# find_each in Rails

An active record reloadtion does not automatically load all records into memory.

When we call `#each`, all records will be loaded into memory.
When we call `#find_each`, records will be loaded into memory in batches of the
given batch size.

So if our query returns a huge number of records, much memory will be used ->
server provides much resources --> Use `find_each` would be a great choice.

It's like using ruby's lazy enumerations `#to_enum#lazy` with `#each_slice` and
`#each`
