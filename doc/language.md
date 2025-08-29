# Language

Streem language consists of constants, variables, operators, etc.

## Code comments

All code comments are prefixed with a hash.

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

## Assigning a variable

Here's how to assign the 42 value to variable x.

```ruby
x = 42
```

Over here, we assign "HELLO, world" to a variable s.

```ruby
s = "HELLO, world"
```

TODO: array, concept of stream, print using stream

## if statements

If statements are done using the keywords 'if' and 'else'. Use "else if" to add more cases

In the following example, "Two" is assigned to the variable s and printed out.

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

```ruby
# Output: HELLO, world

name = "world"
s = "HELLO, " + name
[s] | stdout
```

The s parameter's value is now "HELLO, world".

## Array

Arrays are one of the fundamental data types in Streem.

```ruby
# Output:
# HELLO,
# world

x = ["HELLO,", "world"]
x | stdout
```

## Standard I/O

The 'stdin', 'stdout' and 'stderr' are file descriptors used for the standard I/O operations.

## Stream

Arrays are fundamental data types. Their items are enclosed within square brackets. They can be used with a streaming operator \|.

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

```ruby
# Output: HELLO, world
hello = { name ->
	"HELLO, " + name
}

s = hello("world")
print(s)
```
