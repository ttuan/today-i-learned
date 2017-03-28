# content_for

The purpose of combination of using `content_for` and `yield` is to allow you to
inject data into the application layout form *ANY* view.

For example, in your `application.html.erb` file:

```
<% if content_for?(:navbar) %>
  <%= yield(:navbar) %>
<% else %>
  <%# default navbar %>
  <section class="navbar"></section>
<% end %>
```

And you can change the navbar from any view by using this:
```
<% content_for(:navbar) do %>
  <section class="navbar"></section>
<% end %>
```

==> You can custom view for each page with no pain.

