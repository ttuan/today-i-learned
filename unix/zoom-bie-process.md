# Zoobie process

## What is it?

If you are a linux user, sometime you will see some process named `zombie
process`. Zombie process is a dead process and you can not kill it one more
time =]] Interesting?

Zombie process is a part of ended process but it is not been clear. Some
programs ended and left zombie process. It means the code of those programs is
not good.

## How was it created?

In Linux, there are some process called `parent process`. This is a process to
create other sub process.

When a process end, OS will not delete it imediately. Instead of that, Linux
will hode process discriptor in memory. The status of this process is
EXIT_ZOMBIE and parent of this process will be notified that subprocess die with
SIGCHLD signal.

Mission of parent process is calling wait() function to read status and
infomation of died process. After that, Zombie process will be delete completely
from memory. However, if code of parent process is not good, it will not call
`wait()` func, so zombie process will be in memory until system restart.

## How to kill manualy

If you do not kill zombie process, the PID of unix system will be
misappropriate. If there are many zombie process, the number of PID will very
large, you can not start any process (because linux has limited PID number.)
You can send SIGCHLD to parent process, force it call `wait()` function.

```
kill -s SIGCHLD pid
```

