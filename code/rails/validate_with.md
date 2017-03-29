# Validate With

In Rails validation, when your validate condition belongs to many attributes,
you can not put any field to `validates :field, custom_validator: true`.

`validate_with` can help you. It passes the record off to the class or classes
specified and allows them to add errors based on more complex conditions.

For example: Your message need content OR attachment or both of them.

```
class Message
  validates_with InfoValidator
end

class InfoValidator < ActiveModel::Validator
  def validate record
    record.errors.add :base, :invalid_info if has_no_info(record)
  end

  private
  def has_no_info record
    record.content.blank? && record.attachment.blank?
  end
end
```
