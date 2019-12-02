# Docker build hangs/crashes when useradd with large UID

If you try creating an user and your Dockerfile contains:

```
RUN useradd -u 999999000000 -g users ttuan
```

In domain joined computer, UID of an user usually is large, it causes some
problems with `/var/log/lastlog` file.

To fix this problem, we can add `-l` flag or `--no-log-init` when add an user:

```
RUN useradd -l -u 99999990000000 -g users ttuan
```

