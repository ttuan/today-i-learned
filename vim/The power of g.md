# The power of g
`:[range]g[!]/pattern/cmd`

+ Use `!` means **do not** match pattern
+ Cmd list:
	+ `d`: Delete
	+ `m`: Move
	+ `t`: Copy
	+ `s`: Replace

Example:

```
# Delete all line matching with pattern
:g/pattern/d
# Delete all blank lines
:g/^\s*$/d
# Move all line matching pattern to end of file
:g/pattern/m$
# Add text to end of line matching pattern
:g/^pattern/s/$/mytext
# Run a marco on matching lines
:g/pattern/normal @q
```

You can find more [here](https://vim.fandom.com/wiki/Power_of_g)
