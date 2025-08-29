# Usage

## Normal usage

### no arguments

Start ./streem and input your program that ends with EOF.

### filename

Provide a path to a Streem program as an argument. The filename should end with '.strm'.

```shell
./streem hello_world.strm
```

## -e

Execute one-liners by using the 'e' option.

```shell
./streem -e 'print("HELLO, shell")'
# Output: HELLO, shell
```

## -v

Verbose output about the Streem grammar is available with '-v'.

```ruby
print("HELLO, grammar")
# Output:
# NODES:
#  CALL:
#    print
#    ARRAY:
#     VALUE(STRING): "HELLO, shell"
# HELLO, grammar
```
