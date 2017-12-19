# Rails custom Generator

If you notice when we call some command like `rails g model user`, there are
some lines showed: "Create file app/models/user.rb", "Create file
db/migrate/......", ...

If you want to generate files which have structure, you can create a custom
generator in Rails. For example:

```bash
mkdir lib/generators
touch lib/generators/component_generator.rb
```

```ruby
# lib/generators/component_generator.rb
class ComponentGenerator < Rails::Generators::Base
  argument :component_name, required: true, desc: "Component name, e.g: button"

  def create_view_file
    create_file "#{component_path}/_#{component_name}.html.erb"
  end

  def create_css_file
    create_file "#{component_path}/#{component_name}.css"
  end

  def create_js_file
    create_file "#{component_path}/#{component_name}.js" do
      # require component's CSS inside JS automatically
      "import \"./#{component_name}.css\";\n"
    end
  end

  protected

  def component_path
    "frontend/components/#{component_name}"
  end
end
```

Now, you can call this command to generate your files:

```bash
rails g component NAME
```

(From [this blog](https://evilmartians.com/chronicles/evil-front-part-2))
