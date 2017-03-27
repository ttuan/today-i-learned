# Order In Rails

## Simple order
We use `order` to sort records in some ways. For example: `Post.order
created_at: :desc`

## Reorder
If you want to override previously set order (even through default_scope), use reorder() instead.

```
User.order(id: :asc).reorder(name: :desc)
```
will ignore ordering by id completely

## Ordering on associations
* Using `includes`

    ```
    current_user.conversations.includes(:messages).order("messages.created_at
    DESC")
    ```
* Using `merge`

   ```
   current_user.conversations.joins(:message).merge(Message.order created_at:
   :desc)
   ```

