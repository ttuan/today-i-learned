Which is faster, `<<`, `concat`, or `[a, b].join` ?

a << b and a.concat b are aliased, they should perform the same unless there is some hidden dispatch cost.

[a, b].join will probably be a lot slower as it has to allocate an Array and creates a new String instead of mutating a.
