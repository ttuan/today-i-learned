# Disable Rubocop for special directory

If you want to disable rubocop for special directory, Rubocop has a config to
support it:


```ruby
# rubocop.yml

Metrics/BlockLength:
  Enabled: true
  Exclude:
    - test/**/*
```
