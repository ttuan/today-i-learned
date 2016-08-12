Have you ever used `reload!` command in `rails console` ? I have used this
command many times.

However, today, I know that Rails provides a `reload` command for an *object*

For example, in your rspec test, you define:

```
let!(:user){FactoryGirl.create :user}
let!(:first_post){user.create_first_post}
```

Now, you can see that our first post will have `title: nil, content: nil`. Our
task is ensuring that PostService will update successfully. However, if we call
`PostService.new(user).perform` to update content of post, our `first_post`
still has `nil` title an content because of difference between *object* and
*record*.

So that, if you want to load new content of a post, just use
`first_porst.reload`.
