# MySQL order by boolean

In MySQL, you can order by a boolean value like this:

```sh
SELECT ...
FROM   ...
ORDER BY (gender = 'male') DESC;
```

If gender = 'male' for a row, that row will have a 1/TRUE. Otherwise, it will
have 0/FALSE. => Sorting desc put the rows that have TRUE first.

After that, I try using this command in Rails console: `User.order("TRUE ASC")`,
this command is ok, show list users, order by id. But when I type:
`User.order("FALSE ASC")`, it raises an error. Why?

Cause TRUE ~= 1 => order by TRUE ~= Order by 1 => Order by first column.
Order by FALSE ~= Order by 0 => Order by 0 column => Error
