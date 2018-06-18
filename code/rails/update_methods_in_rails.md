# Update methods in Rails

There are many ways to `update` an attributes of a record in Rails.

* `update_attributes`: Full options, with validate, run callback, update `updated_at` field
* `update_attribute`: Without validate for updated field, run callback, update `updated_at` field
* `update_columns`: Update to DB, without validates, not run callback, not updated `updated_at` field
* `update_column`: Like `updated_columns` but it updates `updated_at` field.
* `update_all`: Update all record in a table without validations, callbacks, `updated_at` field
