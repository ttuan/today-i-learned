## HereDoc in Ruby

In Ruby, you can use `heredoc` to group multiple string line.

For example:
```
<<HEREDOC
multiple string line
....
...
HEREDOC
```

You can use `<<-` instead of `<<`. You can also omit the dash and just write `<<EOT` – if you do this,
your terminating sequence must be at the very beginning of the line. It's less pretty.

`<<~` is also good choice. It can help you auto indent ;)

ActiveSupport in Rails provides a convenient method `string.squish` to remove
all whitespace on both ends of the string. I use this method to remove `\n` in
the last line of multiple string line.
