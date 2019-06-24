# How Rbenv works

In case you don't know what is rbenv: [rbenv](Groom) is a version manage tool, which help to
manage Ruby environment. It's the same as [pyenv](https://github.com/pyenv/pyenv) or [nvm](https://github.com/nvm-sh/nvm).


### rbenv and PATH
rbenv intercepts Ruby commands using shim executables injected into your `PATH`,
determines which Ruby version has been specified by your applicaiton, and passes
your commands along to the correct Ruby installation.

Everytime you run a command like `ruby`, `rake`, ... your OS will searches
through a list of directories to find and executable file with that name. "List
directories" lives in an environment var called `PATH`. You can check by
command: `echo $PATH`.

NOTE: Directories in PATH are searched from left to right.

### Shims script

rbenv works by inserting a directory of `shims` at the front of your `PATH`:

```bash
~/.rbenv/shims:/usr/local/bin:/usr/bin:/bin
```

Through a process called `rehashing`, rbenv maintains shims to match every Ruby command across every
installed version of Ruby - irb, gem, rake, rails, ruby, ...

so, the flow each time you call `rake` is:

* Search your `PATH` for an executable file name `rake`
* Find the rbenv shim named `rake` at the begining of your PATH
* Run the shim named `rake`, which in turn passes the command along to rbenv
