# Great time to make an AJAX call

We can see in lifecycle hook:

![](https://vuejs.org/images/lifecycle.png)

Source: [https://vuejs.org/v2/guide/instance.html](https://vuejs.org/v2/guide/instance.html)

As we can see in this image, `created` hook is a great time to fire an AJAX
call, so it has some time to load, before the component is visible to the user
(in `mount` step)
