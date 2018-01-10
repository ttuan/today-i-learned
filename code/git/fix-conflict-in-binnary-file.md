# Fix conflict in binary file

When you rebase and have a confliction in binary file, you can fix this by using
this command:

```
git checkout --ours -- path/to/conflicted-file.abc

# or

git checkout --theirs -- path/to/conflicted-file.abc
```

