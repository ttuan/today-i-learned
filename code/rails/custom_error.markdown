Rails supports a variable named field_error_proc, allows us to custom error with
form rails.

Each time form has errors, a class will be add to error field automaticly. To
use it, you have to create a file on initializes. for example
```custom_error.rb``` with content:

```
ActionView::Base.class_eval do
  @@field_error_proc = Proc.new do |html_tag, instance|
    unless html_tag =~ /^<label/
      "<div class=\"field_with_errors\">#{html_tag}</div>".html_safe
    else
      html_tag.html_safe
    end
  end
end
```
Now, just custom ```.field_with_errors``` on your css.scss file. Each time form
have error, class .field_with_errors will add to field.
