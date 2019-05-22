# How does cron work?

On [man page](https://www.unix.com/man-page/debian/8/cron/) of cron, I found smt
interesting:

> cron  then  wakes  up  every minute, examining all stored crontabs, checking each command to see if it should be run in the current minute.  When executing commands, any output is mailed to the owner of the crontab (or to the user named in the MAILTO environment variable  in  the crontab, if such exists).  The children copies of cron running these processes have their name coerced to uppercase, as will be seen in the syslog and ps output.

When I run `man cron` on terminal, the same result is shown.

However, this algorithm is too costly. So they found [another solution](https://en.wikipedia.org/wiki/Cron#Multi-user_capability):

1. On start-up, look for a file named .crontab in the home directories of all account holders.
2. For each crontab file found, determine the next time in the future that each command must run.
3. Place those commands on the Franta–Maly event list with their corresponding time and their "five field" time specifier.
4. Enter main loop:
  * Examine the task entry at the head of the queue, compute how far in the future it must run.
  * Sleep for that period of time.
  * On awakening and after verifying the correct time, execute the task at the head of the queue (in background) with the privileges of the user who created it.
  * Determine the next time in the future to run this command and place it back on the event list at that time value.

