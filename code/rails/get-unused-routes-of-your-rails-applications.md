# Get unused routes of your rails app

Learned from [Get unused routes of your rails app](https://medium.com/techies-toolkit/get-unused-routes-of-your-rails-app-be602766fda9)

When our rails applicaiton become larger, there are many unused routes appeared.
You define it in routes.rb file, but you don't define action in controllers.

This script will help to list down all **possible** unused routes

```ruby
Rails.application.eager_load!
unused_routes = {}

# Iterating over all non-empty routes from RouteSet
Rails.application.routes.routes.map(&:requirements).reject(&:empty?).each do |route|
  name = route[:controller].camelcase
  next if name.start_with?("Rails")

  controller = "#{name}Controller"

  if Object.const_defined?(controller) && !controller.constantize.new.respond_to?(route[:action])
    # Get route for which associated action is not present and add it in final results
    unless Dir.glob(Rails.root.join("app", "views", name.downcase, "#{route[:action]}.*")).any?
      unused_routes[controller] = [] if unused_routes[controller].nil?
      unused_routes[controller] << route[:action]
    end
  end
end

puts unused_routes
# {"HomeController"=>["edit", "update", "update", "destroy"]}
```

Just put this code to rails console, or create a file `get-unused-routes.rb` in the root directory of
Rails application and run `ruby get-unused-routes.rb`

