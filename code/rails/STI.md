Single Table Inheritance(STI) allows you to have one signle SQL table but you
can manage different type of object on this table.

For example, in Post table, we have 2 type of post: draft and publish.

In Rails, you can use this code:

```class Post
end
```

```class Draft < Post

end
```

```class Publish < Post

end
```

Rails will generates automatic a field named "type" to save the class name.
