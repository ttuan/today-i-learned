# Shared Example Naming

When you write a shared example in Rspec, please DONT define a file name with postfix `_spec`, which matches the pattern of files RSpec looks to load automatically. Then you are also requiring it somewhere so it is loaded twice.

Or you will get this warning like that:

```
WARNING: Shared example group 'password expired' has been previously defined at:
  /Users/natu/Projects/project-name/spec/support/shared_examples/password_expired_spec.rb:5
...and you are now defining it at:
  /Users/natu/Projects/project-name/spec/support/shared_examples/password_expired_spec.rb:5
The new definition will overwrite the original one.
```
