In rails rspec test, if you're using `factory_girl` to create object test, you
can create multiple objects(a list of objects) with this way:

```
FactoryGirl.create_list(:model_name, 3)
```
