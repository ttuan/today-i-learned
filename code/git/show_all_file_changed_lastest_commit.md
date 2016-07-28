Sometimes, you want to show all changed files in lastest commit, but you don't
want to type: ```git reset HEAD~1``` and ```git diff```, this command will be
useful for you:

> ```git diff @~..@```

```@~``` is alias for ```HEAD``` from git version 1.8.5
You should add an alias to ```.zshrc``` to quickly call it.
