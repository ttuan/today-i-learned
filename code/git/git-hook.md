# Git Hook

![git-hook](https://cdn-images-1.medium.com/max/800/1*gROrgdh5CR-II3v6rZXL7w.png)

Git hooks are scripts that run prior the certain events like commit, push,
rebase, ...

You can check the example of hooks in the folder: `.git/hooks`

```bash
cd .git/hooks
ls

# Output
1. applypatch-msg.sample
2. commit-msg.sample
3. post-update.sample
4. pre-applypatch.sample
5. pre-commit.sample
6. pre-push.sample
7. pre-rebase.sample
8. pre-recieve.sample
9. prepare-commit-msg.sample
10.update.sample
```

So, you can custom those files with your own logic.

For example:

```bash
vim pre-commit
```

and put this content:

```bash
#! /bin/sh

git diff --cached --diff-filter=AM | grep -q "binding.pry"
if [ $? -eq 0 ]
then
  echo "Binding.pry detected. Please remove it and recommit."
  exit 1
fi
```

You can do more with your idea, for example: Run test, lint,... before push :D
If you don't want to use shell script, just write it using `ruby` by change line
`#! /bin/sh` to `#! /usr/bin/ruby` and write code in Ruby

#### Global Hooks
You can create hooks just as above but which apply to all your git repo by
designating a directory that contains all such global hooks, using `git config`
like so:

```bash
git config --global core.hooksPath /path/to/global/hooks
```

Ref: Read more here: [githooks.com](https://githooks.com/)
