# Language

The Streem language consists of constants, variables, operators, and other elements.

## Code comments

All code comments are prefixed with a hash.

### ./streem nil.strm

```ruby
# minimal program that can be called NIL
```

## Types

| Value | Type |
| :---: | :---: |
| "HELLO, world" | string |
| true, false | boolean |
| 42 | integer |
| 4.2 | float |
| [1,2,3] | array |
| x -> x | function |
| map, flatmap etc | built-in function |
| stdin, stdout etc | file descriptor |
| x \| y | x can be a stream |

## Standard output with streams

It's possible to pipe an array into standard output without calling a function. Just use the bar operator. This construct
will be used in the sections covering the language features. Calling 'print()' or 'puts()' can be preferred elsewhere.

#### ./streem hobbies.strm

```ruby
hobbies = ["yoga", "Tai Chi", "Qigong", "foreign languages", "my blog"]
hobbies | stdout

# Output:
# yoga
# Tai Chi
# Qigong
# foreign languages
# my blog
```

## Assigning a variable

### ./streem assign-42.strm

Here's how to assign the 42 value to variable x.

```ruby
x = 42
```

### ./streem assign-hello.strm

Over here, we assign "HELLO, world" to a variable s.

```ruby
s = "HELLO, world"
```

TODO: array, concept of stream, print using stream

## Arithmetic expressions

Use the basic arithmetic operators to perform computations.

| Operator | What is? |
| :---: | :---: |
| + | sum |
| - | difference |
| * | multiplication |
| / | division (float) |
| % | remainder |

### ./streem operators.strm

```ruby
x_1 = 2 + 3 # 5
x_2 = x_1 * 4 # 20
x_3 = x_2 / 4 # 5
x_4 = x_3 - 3 # 2
x_5 = x_4 % 2 # 2
[x_1, x_2, x_3, x_4, x_5] | stdout

# Output:
# 5
# 20
# 5
# 2
# 0
```

## Logical expressions

> Logical operators are not implemented. Source code that uses them won't parse.

There's an '\|\|' operator for logical "or", and '&&' operator for logical "and".

## Parentheses

You can enclose expressions in brackets to formulate more complex expressions.

### ./streem multiplication.strm

```ruby
# Output: 20

x = (2 + 3) * 4
[x] | stdout
```

## if statements

If statements are done using the keywords 'if' and 'else'. Use "else if" to add more cases

In the following example, "Two" is assigned to the variable s and printed out.

### ./streem one-or-two.strm

```ruby
# Output: Two
x = 2

if (x == 1) {
  s = "One"
} else if (x == 2) {
  s = "Two"
} else {
  s = "Unknown"
}

[s] | stdout
```

## Concatenate strings

Strings can be concatenated with the plus operator. Here's an example that can be part of a traditional Hello World program.

### ./streem pipe-hello-world.strm

```ruby
# Output: HELLO, world

name = "world"
s = "HELLO, " + name
[s] | stdout
```

The s parameter's value is now "HELLO, world".

## Array

Arrays are one of the fundamental data types in Streem. They are declared as \[x_1, x_2, ..., x_3\].

## Standard I/O

The 'stdin', 'stdout' and 'stderr' are file descriptors used for the standard I/O operations.

## Stream

Arrays are fundamental data types. Their items are enclosed within square brackets. They can be used with a streaming operator \|.

### ./streem pipe-hello-world-multiline.strm

```ruby
x = ["HELLO,", "world"]
x | stdout

# Output:
# HELLO,
# world
```

The 'stderr' file descriptor could have also been used in this example.

## Functions

Functions are defined within the curly brackets in a lambda-expression manner. Arguments are used, and the last expression is the return value.

### ./streem hello-world-function.strm

```ruby
# Output: HELLO, world
hello = { name ->
	"HELLO, " + name
}

s = hello("world")
print(s)
```

### Functions with multiple parameters

To pass multiple arguments to a function, a matching number of parameters needs to be declared and surrounded by brackets. More than 2 parameters are allowable.

### ./streem add.strm

```ruby
add = (x, y) -> x + y
addz = (x, y, z) -> {
	xy = add(x, y)
	add(xy, z)
}

a = 123456789
b = 987654321

puts(add(a, b))
puts(addz(a, b, 1))

# Output:
# 1111111110
# 1111111111
```
