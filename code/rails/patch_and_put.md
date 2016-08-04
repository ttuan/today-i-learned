In Rails, if you run `rake routes`, you will see 2 type of method: PUT and
PATCH, both of them are redirect to `model#update`. So what are difference
between PUT and PATCH.

The most difference is PATCH is `partial update` and PUT is `full update`.

For example, if your record has 8 fields, and you just want to update 2 fields
on this, PATCH will update those 2 fields, but PUT will update 2 fields AND
others are set to default/existing values.
