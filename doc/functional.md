# Functional programming

Functions are provided to use typical functional programming.

## filter() - filters a stream

A stream can be filtered to find values matching a predicate.

### ./streem find-larger.strm

Values 100, 200, and 300 are filtered out because they are less than or equal to 300, and therefore don't match the predicate.

```ruby
array = [100, 200, 300, 400, 500]
predicate = filter { x -> x > 300 }
array | predicate | stdout

# Output:
# 400
# 500
```
