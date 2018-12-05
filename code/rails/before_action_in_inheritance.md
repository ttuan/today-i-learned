# before_action in inheritance

Everbody know what `before_action` do, but today, I find some interesting thing with `before_action` in inheritance.

For example:

```ruby
class Api::V1::BooksController < Api::V1::BaseController
  before_action :authenticate_user, only: %i(create update)

  def create
    # stuff here
  end

  def update
    # stuff here
  end
end

class Api::V2::BooksController < Api::V1::BooksController
  before_action :authenticate_user, only: :show

  def show
    # ...
  end
end
```

I wanna call authenticate_user for both method: `show` in `ChildController` and `create, update` for `ParentController`, but if I write code like above, `authenticate_user` will be called ONLY for action `show`. If POST request comes from:
`/api/v2/books`, `authenticate_user` will NOT be called.

* Solution

Call the method inside a block inside child controller instead of passing it by name.

```ruby
class Api::V2::BooksController < Api::V1::BooksController
  before_action(only: :show){authenticate_user}

  def show
    # ...
  end
end
```
