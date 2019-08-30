# Git delete multiple branches

We can delete multiple branches in Git with this command:

`git branch | grep "<parttern>" | xargs git branch -D`

For example:

`git branch | grep "pullrequest/pr" | xargs git branch -D`
