# Mail problem in Rails

As humans, we have problems with doing things in parallel. The same as coding :v

When a user sends invitation to his friend, we get information from Sidekiq, but
this invitation is not found in database. why?

```ruby
class Invitation < ActiveRecord::Base
  after_save :send_invitation_email

  # (...)

  def send_invitation_email
    AppMailer.invitation_email(
      user_id: user.id, recipient_email: email, invitation_id: self.id
    ).deliver_later
  end
end
```

The problem is we are using `after_save`, and `after_save` isn't the last one in
list Rails callbacks:

```bash
before_validation
after_validation
before_save
around_save
before_create
around_create
after_create
after_save
after_commit/after_rollback
```

So when `send_invitation_email` is called, I still have id, but this invitation
is not persist in the database yet (cause data is not committed to database).
Looking below on this scheme actions(1) and (2), are faster than (3)

![](https://womanonrails.com/images/rails-mailer-problem/mailer-in-rails-model.jpg)

The solution is changing `after_save` to `after_commit` to ensure data is saved
in database, or a better way, split this logic to service, SHOULD NOT use
callback cause it's pain to handle latter.

When you move this code to service, BE CAREFULL WITH TRANSACTION. Transaction
and mailer will work in parallel, and this can lead to the same problem.

```ruby
  def perform
    ActiveRecord::Base.transaction do
      admin.update! password: password
      admin.request_password_change!
    end
  rescue ActiveRecord::RecordInvalid
    response_data false
  else
    Admin::AdminMailer.resend_password_admin(admin, password).deliver_later
    response_data true
  end
```

Use else block to ignore parallel problem!

