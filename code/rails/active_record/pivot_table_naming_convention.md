# Pivot table's naming convention

If we have 2 tables `authors`, `books` and a `has_and_belongs_to_many`
relationship, we need to create a pivot table. But is there any naming
convention for this pivot table name?

Refer here:
https://guides.rubyonrails.org/association_basics.html#creating-join-tables-for-has-and-belongs-to-many-associations

We need add pivot table named `authors_books` (not `books_authors` or
`author_books`) caused `a` outranks `b` in lexical ordering.

But the model name just is: `author_book`.

The pivot table is not need a primary key. So we pass `id: false` to `create_table` because that table does not represent a model.

```ruby
class CreateAuthorsBooksJoinTable < ActiveRecord::Migration[5.2]
  def change
    create_table :authors_books, id: false do |t|
      t.bigint :author_id
      t.bigint :book_id
    end

    add_index :authors_books, :author_id
    add_index :authors_books, :book_id
  end
end
```
