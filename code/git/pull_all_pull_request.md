If you want to check pull request of someone, this is one of easy ways.

First, add this code to your `.git/config` file on your profject

```
[remote "pullrequest"]
  url = https://github.com/username/repo_name
  fetch = +refs/pull/*/head:refs/remotes/pullrequest/pr/*
```

Now, if you want to pull all pullrequest, just call: `git pull pullrequest` to
pull all pullrequest to local.

To check a pull, type: `git checkout pullrequest/pr/<pull_number> -b
branch_test_name`.

