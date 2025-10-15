# Standard

Streem has standard functions for processing strings, I/O, CSV, hashtables and bar graphs.

## Built-in objects

### Standard I/O

The 'stdin', 'stdout' and 'stderr' are file descriptors used for the standard I/O operations.

## Built-in functions

Stream contains a variety of built-in functions.  Note that they can return streams.

### puts() - print a string to standard output

The puts() function can be used for printing to standard output.

#### ./hello-world.strm

```ruby
# Output: HELLO, world
s = "HELLO, world"
puts(s)
```

### print() - print to standard output

The print() function is an alias to the puts() function.

### Reverse an array

An array can be reversed using a 'reverse' function. Instead of a new array, a stream is created.

#### ./countdown.strm

```ruby
x = [1, 2, 3]
reverse(x) | stdout
# Output:
# 3
# 2
# 1
```

### exit(status)

Terminates with a specified value. Useful in Shell scripts.

#### ./success.strm

```ruby
./streem -e "exit(1)" || echo "failure"
# Output: failure
```

#### ./failure.strm

```ruby
./streem -e "exit(0)" && echo "success"
# Output: success
```

### zip() - zip two streams

Creates a quasi-dictionary structure that consists of the keys given in the left argument and values in the right argument.
Both arguments are arrays. The output array consists of an array of two-element arrays. The first is the key, and the second is the value.

### ./sheet.strm

```ruby
rows = [["cell_1", "cell_2", "cell_3"],
        ["cell_4", "cell_5", "cell_6"],
        ["cell_7", "cell_8", "cell_9"]]
columns = ["column_1", "column_2", "column_3"]
zip(columns, rows) | stdout

# Output:
# ["column_1", ["cell_1", "cell_2", "cell_3"]]
# ["column_2", ["cell_4", "cell_5", "cell_6"]]
# ["column_3", ["cell_7", "cell_8", "cell_9"]]
```

### & - zip two arrays

The & operator is an alias to the zip() function.

#### ./matrix.strm

```ruby
seq(3) & seq(3) | stdout
[1, 1]
[2, 2]
[3, 3]

# Output:
# [1, 1]
# [2, 2]
# [3, 3]
```

### ./zip-with-counter.strm

You can zip streams as well, not just arrays.

```ruby
# Input:
# HELLO,
# @stagyrite
# 🐍

stdin & seq(3) | stdout

# Output:
# ["HELLO,", 1]
# ["@stagyrite", 2]
# ["🐍", 3]
```

### Streaming bar graph

A trivial example that counts down from 3 to 0.

#### ./stag-countdown.strm

```ruby
graph = graph_bar()
[3, 2, 1, 0] | graph
```

It can be filled with numbers from the range 1 to 250.

#### stag-linear.strm

```ruby
graph = graph_bar()
seq(250) | graph
```

### Random numbers

> The random number generator is not fully implemented. Random numbers can be acquired only by modifying the source code.

There's an ability to generate random numbers.

#### rand_seed() - generate a random seed

It generates a string that can be used as a random seed.

#### rand() - instantiate a stream of random numbers

It takes one argument, which is a random seed. If no arguments are provided, it uses a randomly generated seed.

It starts to emit floating-point numbers. e.g., 0.978470, 0.396758, 0.241088, etc.

#### rand_norm() - instantiate a streem of normal (or Gaussian) random numbers

Generate Gaussian noise using the Marsaglia polar method.

#### sample() - retrieves a sample of data

Pass a number n to retrieve the n-th element from a stream.

### String manipulation

Strings can be transformed and manipulated with a set of built-in functions.

#### number() - converts a string to a number

You need to parse out an integer or a floating-point number from a string, possibly user input. The 'number()' function returns a number that can be used with mathematical operators.

```ruby
# Output: 58
eight = number("8")
seven = number("7.0")
puts(eight * seven)
```
