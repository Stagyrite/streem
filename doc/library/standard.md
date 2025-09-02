# Standard

Streem has standard functions for processing strings, I/O, CSV, hashtables and bar graphs.

## Built-in objects

### Standard I/O

The 'stdin', 'stdout' and 'stderr' are file descriptors used for the standard I/O operations.

## Built-in functions

### puts() - print a string to standard output

The puts() function can be used for printing to standard output.

#### ./hello-world.strm

```shell
# Output: HELLO, world
s = "HELLO, world"
puts(s)
```

### print() - print to standard output

The print() function is an alias to the puts() function.

Stream contains a variety of built-in functions. Note that functions tend to return streams.

### Reverse an array

An array can be reversed using a 'reverse' function. Instead of a new array, a stream is created.

#### ./countdown.strm

```shell
x = [1, 2, 3]
reverse(x) | stdout
# Output:
# 3
# 2
# 1
```

### Sequence of numbers

To produce a sequence of numbers (1, 2, 3, ..., n) for a given n, call the 'seq' function.

#### ./counter.strm

```shell
seq(3) | stdout

# Output:
# 1
# 2
# 3
```

### exit(status)

Terminates with a specified value. Useful in Shell scripts.

#### ./success.strm

```shell
./streem -e "exit(1)" || echo "failure"
# Output: failure
```

#### ./failure.strm

```shell
./streem -e "exit(0)" && echo "success"
# Output: success
```

### zip() - zip two streams

Creates a quasi-dictionary structure that consists of the keys given in the left argument and values in the right argument.
Both arguments are arrays. The output array consists of an array of two-element arrays. The first is the key, and the second is the value.

### ./sheet.strm

```shell
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

```shell
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

```shell
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

```shell
graph = graph_bar()
[3, 2, 1, 0] | graph
```

It can be filled with numbers from the range 1 to 250.

#### stag-linear.strm

```shell
graph = graph_bar()
seq(250) | graph
```
