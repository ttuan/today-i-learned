`chmod` is a unix command which may change access permissions of a file or
folder (read, write or execute)

+ Read is specified by number 4
+ Write is specified by number 2
+ Execute is specified by number 1


`chmod` change permission of 3 type of users:

+ Owner: the owner of file/ folder
+ Group: The group which "owner" of file is a member
+ Public/Others/Everybody: rest of others

So, `chmod 755` means:

![chmod](http://farm3.staticflickr.com/2841/32873005342_865636215d_o.png)


### Now we talk about the first octet

When you type `chmod 775 file`, that actually means: `chmod 0775 file`

The first octet works the same way as the other three as it has 3 possible values that add to make the octet:

```
4 - setuid (letter-style: s)
2 - setgid (letter-style: s)
1 - sticky bit (letter-style: t)
```

* setuid
If you `setuid` on a binary, you’re telling the operating system that you want this binary to always be executed as the user owner of the binary. So, let’s say the permissions on a binary are set like so.

```
# chmod 4754 reader
# ls -al reader
-rwsr-x--- 1 root users 0 Feb 13 21:43 reader
```

It means everyone in `users` group is able to run this file `reader`. However, when the binary runs, it will run with `root` permissions. *Anything higher than 4750 can be very dangerous as it allows the world to run the binary as the root user.*

Example:

```
$ ls -l
-rwxr-x--- 1 root users 47904 Oct  3 11:10 reader
-rwx------ 1 root users    15 Oct  3 11:11 rootfile.txt

$ ./reader rootfile.txt
./reader: rootfile.txt: Permission denied

# chmod 4750 reader

$ ls -l
-rwsr-x--- 1 root users 47904 Oct  3 11:10 reader
-rwx------ 1 root users    15 Oct  3 11:11 rootfile.txt

$ ./reader rootfile.txt
SECRET_CONTENT
```

* setgid
`setuid` is pretty much the exact same as setuid, but the binary runs with the privileges of the owner group rather than the user’s primary group privileges. 

* sticky bit

After applying this bit on the directory, the users have permisison to do anything they want to files they created. Like so, they can't write to or delete files which they didn't create.

```
# chmod 1777 /tmp
# ls -ld /tmp
drwxrwxrwt 3 root root 4096 Feb 13 21:57 /tmp
```

> Refer: https://major.io/2007/02/13/chmod-and-the-mysterious-first-octet/
