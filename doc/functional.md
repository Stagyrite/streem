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

## flatmap - flattens the input stream

You can make an array out of a matrix (array of arrays) by calling 'flatmap()'. Just pass the identity function as its argument, i.e. the '{ x -> x }' lambda expression. Note that the 'x' variable in the expression is by itself a stream.

```ruby
matrix = [[1, 2], [3, 4]]
identity = { x -> x }
matrix | flatmap(identity) | stdout

# Output:
# 1
# 2
# 3
# 4
```

## Sequence of numbers

To produce a sequence of numbers (1, 2, 3, ..., n) for a given n, call the 'seq' function.

### ./counter.strm

```ruby
seq(3) | stdout

# Output:
# 1
# 2
# 3
```

## reduce - reduce a stream to an object

To reduce a stream, pass the reduction function as the 'reduce' function argument.

### ./streem sum-numbers.strm

In this example, the sequence of numbers from 1 to 50 is summed. It can be done using a mathematical theorem, and the result is 1275. The Streem function that does it is '{ x -> x * (x + 1) / 2 }'.

```ruby
# Output: 1275

seq(50) | reduce { x, y -> x + y } | stdout
```
