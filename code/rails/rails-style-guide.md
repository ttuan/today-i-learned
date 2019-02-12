# Rails style Guide

* Should use `find_each` to iterate over a collection of ActiveRecord Objects.  (instead of `all`)

```
  # bad
  Person.all.each do |person|
    person.do_awesome_stuff
  end

  Person.where('age > 21').each do |person|
    person.party_all_night!
  end

  # good
  Person.find_each do |person|
    person.do_awesome_stuff
  end

  Person.where('age > 21').find_each do |person|
    person.party_all_night!
  end
```

* Prefer `corresponding symbols` to numeric HTTP status codes. They are meaningful and do not look like "magic" numbers for less known HTTP status codes.

```
# bad
...
render status: 403
...

# good
...
render status: :forbidden
...
```

* Favor the use of `ids` over `pluck(:id)`

```
# bad
User.pluck(:id)

# good
User.ids
```


