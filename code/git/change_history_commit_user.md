To set up right name and email in the future for commits, you need run
command:

```
git config --global user.name "username"
git config --global user.email "username@example.com"
```
or put this in ~/.gitconfig file.

If you want to FIX pervious unauthored commits:

1. `gith show` to show WHICH WRONG email has been used.
2. Create a bare cllone of repo:
`git clone --bare https://github.com/username/repo.git`
3. Replace OLD_EMAIL, CORRECT_NAME, CORRECT_EMAIL after `cd` to the repo and
   save this script in your `repo.git` with name `change_user.sh`

   ```
   #!/bin/sh

    git filter-branch --env-filter '

    OLD_EMAIL="your-old-email@example.com"
    CORRECT_NAME="Your Correct Name"
    CORRECT_EMAIL="your-correct-email@example.com"

    if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
    then
        export GIT_COMMITTER_NAME="$CORRECT_NAME"
        export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
    fi
    if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
    then
        export GIT_AUTHOR_NAME="$CORRECT_NAME"
        export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
    fi
    ' --tag-name-filter cat -- --branches --tags
  ```
  run command: `chmod +x change_user.sh && ./change_user.sh`

4. Force push to Github:
`git push --force --tags origin 'refs/heads/*'`
