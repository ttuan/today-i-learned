# Rails error handler order

If you want to rescue multiple errors, you should declare general handlers
first. (eg: one for `StandardError`) then specific ones.

For example:

```ruby
rescue_from StandardError, with: :internal_server_error
rescue_from CustomError, with: :custom_error
rescue_from XXXError, with: :xxx_error
```
By this way, StandardError > CustomError > XXXError.

Reference: https://github.com/rails/rails/blob/66cabeda2c46c582d19738e1318be8d59584cc5b/activesupport/lib/active_support/rescuable.rb#L124-L126
