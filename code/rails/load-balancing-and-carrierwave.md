# Carrierwave and Load Balancing problem

When you deploy web app, store image on S3, using Load balancing, you may face
with this problem:

Pre-Condition: For example, in edit user information page:
+ (1) User fill information into a form, and click button select file avatar (still in this form)
+ (2) User submit form, but validations fail, and Rails app rerender this form.
+ (3) User correct the form, and resubmit => Save success
+ (4) When you go to detail page, => Error -> Can not load the file avatar of user.

The reason why you can not load file avatar is the avatar is still not saved on S3.

In LB, assume that we have 2 instances.

+ At step (2), when validations fail, carrierwave pass cache file to form.  (through `file_cache` attribute). But this temp file is storaged in (rails_repo/public/tmp/...) of Instance 1 of LB.
This cache file is just a unique string.
+ At step (3), when user resbumit form, carrierwave will find temp file in storaged dir by using the unique string.

But problem is, at step (3), the request can come to Instance 2 of LB => Carrierwave can not find the file with that unique string, but RECORD IS STILL SAVED.

That why when you come to user detail page, you can not see avatar image, maybe a page with status 500 can be shown.
