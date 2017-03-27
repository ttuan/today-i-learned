# Counter Cache

## What is counter cache?

Counter cache used to cache the number of belonging objects on associations.

## How

For example, we want to count the number of comments on each post record.

```Ruby
class Post < ActiveRecord::Base
  has_many :comments
end

class Comments < ActiveRecord::Base
  belongs_to :post
end
```
The first thing you have to do is adding a `comments_count` column on Post
table. After that, you change on Comments model:

```
belongs_to :post, counter_cache: true
```

Each time you add a new comment, this field will increase automaticly. The only problem left is that the counts are off if there are already posts and comments in the database.
