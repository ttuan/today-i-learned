When your app becomes more bigger, your `routes` will has many lines.

In this case, please split it into some small file(you can split by namespace).
put it in `config/routes` folder and load it when server starts by add some
lines in `config/application.rb` :

```
config.paths["config/routes.rb"] << Rails.root.join("config", "routes", "admin.rb")
config.paths["config/routes.rb"] << Rails.root.join("config", "routes", "rule.rb")
config.paths["config/routes.rb"] << Rails.root.join("config", "routes", "search_rule.rb")
```
