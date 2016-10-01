If you delete a branch in git and you want to undo this action, you want to take
all code of deleted branch.
You can use `git reflog` to find SHA1 of the last commit branch. From that
point, you can recreate a branch using this command:

`git branch branch_name sha1_code`

Git change the world :v
