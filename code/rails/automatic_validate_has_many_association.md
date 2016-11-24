In Rails, you have a `Question` and `Answer` model.

```
question = Question.new
question.answers.build
question.valid?
```

This will return `false` because the associated answer is not valid. It's most
definitely not a bug because you are then asking "Rails, is this Question/Answer
model and association I've created ready to be saved to the database?" and Rails
say "No" in this case.


To ignore validate in associated model, you must put this code in `Answer`
model: `has_many: answers, validate: false`


