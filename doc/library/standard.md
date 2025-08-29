# Standard

Streem has standard functions for processing strings, I/O, CSV, hashtables and bar graphs.

## Built-in objects

### Standard I/O

The 'stdin', 'stdout' and 'stderr' are file descriptors used for the standard I/O operations.

## Built-in functions

### puts() - print a string to standard output

The puts() function can be used for printing to standard output.

```ruby
# Output: HELLO, world
s = "HELLO, world"
puts(s)
```

### print() - print to standard output

The print() function is an alias to the puts() function.

Stream contains a variety of built-in functions. Note that functions tend to return streams.

### Reverse an array

An array can be reversed using a 'reverse' function. Instead of a new array, a stream is created.

```ruby
x = [1, 2, 3]
reverse(x) | stdout
# Output:
# 3
# 2
# 1
```

### Sequence of numbers

To produce a sequence of numbers (1, 2, 3, ..., n) for a given n, call the 'seq' function.

```ruby
seq(3) | stdout

# Output:
# 1
# 2
# 3
```

### exit(status)

Terminates with a specified value. Useful in Shell scripts.

```shell
./streem -e "exit(1)" || echo "failure"
# Output: failure
```

```shell
./streem -e "exit(0)" && echo "success"
# Output: success
```

### Streaming bar graph

A trivial example that counts down from 3 to 0.

```ruby
graph = graph_bar()
[3, 2, 1, 0] | graph
```

It fills it with numbers from the range 1 to 250.

```ruby
graph = graph_bar()
seq(250) | graph
```
