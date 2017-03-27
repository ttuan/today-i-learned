# Open PDF file on Rails

To open PDF file on Rails, we write a simpler controller like other. However, we
will use `send_file` like download pdf function:

```Ruby
class Term::UserController < ApplicationController
  def new
    send_file(
      "#{Rails.root}/public/#{Settings.term_of_use}",
      filename: Settings.term_of_use,
      type: "application/pdf",
      disposition: "inline"
    )
  end
end
```

and in view file, we just use:
```
<%= link_to t(".term_of_use"), new_term_user_path, target: "_blank" %>
```
