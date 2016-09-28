In IRB, we can use vim to type a block of code easily. To do this imposible, all you need to do is
create a file `~/.irbrc` with content:

```
require 'rubygems'
require 'interactive_editor'
```

Don't forget to run `gem install interractive_editor` before you do this.
Now, in irb terminal, just call `vi` or `vim`, enter the block code and save it, this code will be
run on irb.

Be nice with `IRB` and `VIM`. :)
