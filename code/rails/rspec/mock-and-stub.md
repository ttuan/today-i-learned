# Difference between Mocks and Stubs

**Stub**:

> Returns canned response, avoiding any meaningful computation or I/O

Example:

```ruby
allow(some_object).to receive(some_method).and_return(some_value)
```

**Mock**:

> Expects specific messages; will raise an error if it doesn't receive them by the end of the example

```ruby
expect(some_object).to receive(some_method).and_return(some_value)
```

Mocks are all about expectations for a method to be called, whereas stubs are just about allowing an object to respond to method call with some value.

Mock like testing out going methods.
Stubs use double to fake data.
