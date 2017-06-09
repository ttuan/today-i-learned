# Vietnamese search key in MySQL

MySQL can not recognize Vietnamese key, for example: "my" and "mỹ" will be
treated same.

If u want to search with Vietnamese key, you should convert the key to BINARY.

For example

```
SELECT * FROM hashtags WHERE hashtag LIKE '%mỹ'
```
