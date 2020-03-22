# Rails ActionController::ParamsWrapper


Rails auto wraps the parameters hash into a nested hash. This will allow clients to submit requests without having to specify any root elements.

This functionality is enabled in `config/initializers/wrap_parameters.rb` and can be customized.

For example: If you send POST request to create user with information:

```json
{
  "name": "Bob",
  "age": 20
}
```

It will be wrapped into a nested hash with the key name matching the controller's name.

```json
{
  "name": "Bob",
  "age": 20,
  "user": {
    "name": "Bob",
    "age": 20
  }
}
```

You can custom it on per controller.

Ref: https://api.rubyonrails.org/v6.0.2.1/classes/ActionController/ParamsWrapper.html

