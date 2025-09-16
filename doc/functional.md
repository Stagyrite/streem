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

## take() - take some elements from a stream

Instantiates a new stream that consists of some elements from an input stream. The number of elements is passed as an argument.

```ruby
random = [0.978470, 0.396758, 0.241088, 0.543190, 0.598714, 0.451562, 0.944703]
random | take(3) | stdout

# Output:
# 0.97847
# 0.396758
# 0.241088
```
