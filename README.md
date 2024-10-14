# Understanding Binary

In this section, we will cover the following topics:

- Introduction to Binary Numbers
  - Binary Representatoin
  - Convert Decimal Numbers to Binary
  - Convert Binary Numbers to Decimal
  - Intoduction to a Bit
- Binary Arithmetic
  - Binary addition, subtraction, multiplication, and division
  - Overflow in binary arithmetic
- Bitwise Operators in Python
  - AND (&), OR (|), XOR (^), NOT (~)
  - Bit shifting (left shift << and right shift >>)
- Applications of Binary in Python
  - Binary search algorithm (basic introduction to searching using binary logic)
  - Binary file handling in Python (using open() in binary mode)
  - Practical use cases (e.g., working with binary data, encryption basics, etc.)
- Boolean Logic and Binary
  - Boolean values (True/False)
  - Relating binary values (0/1) to False and True
  - Boolean operations (and, or, not) in Python and their binary equivalents
- Binary Conversion Functions in Python
  - Decimal to binary (bin())
  - Binary to decimal (int(binary_str, 2))
  - Decimal to hexadecimal (hex())
  - Binary to hexadecimal conversions
- Floating Point Numbers and Binary
  - Basic explanation of floating-point representation in binary
  - IEEE 754 floating-point standard (overview)
  - Understanding precision errors with floating-point numbers

While it's not essential that you have a deep understanding of Python to complete this lesson, it's recommended that you have a basic understanding of Python syntax and data types.

## Introduction to Binary Numbers

Okie dokie artichokie! Let's dive into the world of binary numbers. Binary numbers are a fundamental concept in computer science and digital electronics. They got their start all the way back in the 17th century with the invention of the binary number system by Gottfried Wilhelm Leibniz.

This system uses only two digits, 0 and 1, to represent numbers. It's the foundation of all digital systems, including computers, smartphones, and other electronic devices.

### Binary Representatoin

Each binary number represents a power of 2. This is due to the base-2 nature of the binary system. *Base-2 meaining there are only two digits: 0 and 1.* The rightmost digit represents 2^0 (1), the next digit to the left represents 2^1 (2), the next represents 2^2 (4), and so on.

The wonderful thing about this is that we do not have to memorize the powers of 2. We will see how we can leverage Python to convert decimal numbers to binary and vice versa. The main take away here is to know that binary numbers are made up of 1s and 0s and bonus points if you can recall that this is called the base-2 numbering system.

Let's take a look at a few examples:

```plaintext
Nubmer: 15
Binary: 1111

Number: 8
Binary: 1000

Number: 3
Binary: 11
```

> tktk Visual representation of counting in binary can be viewed here. (create and add image)

### Convert Decimal Numbers to Binary

Enough chit-chat! Let's get down to business and convert some decimal numbers to binary. Feel free to follow along in a Python REPL or your favorite code editor.

Let's start with the number 15. We know that 15 in binary is 1111. But how do we get there?

```python
binary_number_15 = '1111'
```

We can use the built in Python function `int()` to convert a decimal number to binary. by default, `int()` converts a number to a base-10 number which is the decimal system. However, we can change that behavior by passing in a second argument to `int()`. However, we can change that default behavior of converting to a base-10 number to a base-2 number by passing in a second argument to `int()`.

```python
binary_number_15 = '1111'
decimal_number_15 = int(binary_number_15, 2)
```

By printing `decimal_number_15`, we should see `15` as the output. It's just that simple!

### Convert Binary Numbers to Decimal

Now that we know how to convert decimal numbers to binary, let's flip the script and convert binary numbers to decimal. We can use the built-in Python function `bin()` to convert a decimal number to binary. By default, `bin()` returns a string representation of the binary number.

```python
decimal_number_15 = 15
binary_number_15 = bin(decimal_number_15)
```

Yup, it's that easy! By printing `binary_number_15`, we should see `'0b1111'` as the output. The `0b` prefix indicates that the number is in binary form.

### Intoduction to a Bit

Lastly before we dive into using binary numbers in Python, let's talk about bits. What is a bit? A bit or binary digit is the most basic unit of data in computing and digital communications. It can have one of two values: 0 or 1. *AKA binary numbers!*

When we look at the number `15` in binary `1111`, we see that it is made up of 4 bits. As our decimal number grows, so does the number of bits required to represent it in binary. 8 bits make a byte, and 1024 bytes make a kilobyte. This is the basis of digital storage and memory.

## Binary Arithmetic

Now that we have a basic understanding of binary numbers, let's dive into binary arithmetic. We will cover binary addition, subtraction, multiplication, and division. We will also discuss overflow in binary arithmetic.

### Binary Addition

Binary addition is similar to decimal addition, but with only two digits: 0 and 1. 

Let's start with some binary numbers:

```python
binary_1 = '1010' # Binary for decimal 10
binary_2 = '1101' # Binary for decimal 13
```

First convert them on over to decimals using the `int()` function:

```python
binary_1 = '1010'
binary_2 = '1101'

decimal_1 = int(binary1, 2) # Convert to decimal number 10
decimal_2 = int(binary2, 2) # Convert to decimal number 13
```

I know it might seem like we are loosing the binary numbers, but we will get them back. Let's add the decimal numbers together:

```python
binary_1 = '1010'
binary_2 = '1101'

decimal_1 = int(binary1, 2)
decimal_2 = int(binary2, 2)

sum_decimal = decimal_1 + decimal_2 # 10 + 13 = 23
```

Now that we have the sum of the decimal numbers, we can convert it back to binary using the `bin()` function:

```python
binary_1 = '1010'
binary_2 = '1101'

decimal_1 = int(binary1, 2)
decimal_2 = int(binary2, 2)

sum_decimal = decimal_1 + decimal_2

binary_sum = bin(sum_decimal) # '0b10111'
```

Finally we can do this in one line if we wanted to:

```python
binary_1 = '1010'
binary_2 = '1101'

binary_sum = bin(int(binary_1, 2) + int(binary_2, 2)) # '0b10111'
```

### Binary Subtraction, Multiplication, and Division

Since we have seen the trick to adding binary numbers, we can apply the same logic to subtraction, multiplication, and division. The key is to convert the binary numbers to decimal, perform the operation, and then convert the result back to binary.

```python
binary_1 = '1010'
binary_2 = '1101'

binary_diff = bin(int(binary_1, 2) - int(binary_2, 2)) # '0b111'
binary_product = bin(int(binary_1, 2) * int(binary_2, 2)) # '0b11010'
binary_quotient = bin(int(binary_1, 2) // int(binary_2, 2)) # '0b0'(floor division)
```

### Overflow in Binary Arithmetic

A couple of sections back we briefly mentioned that a bit is the smallest unit of data in computing and hat it can have one of two values: 0 or 1. When represent the number `15` in binary we use 4 bits `1111`. But what happens if we need to add another bit to represent a larger number?

This is where overflow comes into play. Overflow occurs when the result of an arithmetic operation exceeds the maximum value that can be represented by the number of bits available. In our example, if we try to add `1` to `15` in binary `1111`, we would get `10000`. However, we only have 4 bits available, so the result would overflow and the leftmost bit would be lost.

With Python, by default we don't need to worry about overflow. Python automatically handles the overflow by increasing the number of bits to accommodate the result. We can however simulate overflow by using the `&` operator to limit the number of bits.

```python
binary_1 = '1111'
binary_2 = '1'

max_bits = 4

binary_sum = bin(int(binary_1, 2) + int(binary_2, 2)) # '0b10000'
binary_sum_overflow = bin(int(binary_1, 2) + int(binary_2, 2) & max_bits) # '0b0'
```

We can see in `binary_sum_overflow` that the result is `0` because the leftmost bit was lost due to overflow. Now we no longer have the binary number of `16` but `0`. Again we don't have to worry about this in Python, but it's good to know how it works under the hood.

## Bitwise Operators in Python

Let me tell you a pretty cool secret. Python treat numbers as binary behind the scenes. This means that we can perform bitwise operations on numbers. Bitwise operators are used to manipulate individual bits of a number. 

| **Operator** | **Symbol** | **Description**                                               | **Example**                                                  |
|--------------|------------|---------------------------------------------------------------|--------------------------------------------------------------|
| AND          | `&`        | Compares each bit and returns `1` if both sides are `1`, otherwise returns `0`| `1101 & 1011 = 1001` (13 & 11 = 9) |
| OR           | `\|`       | Compares each bit and returns `1` if at least one of the bits is `1`, otherwise returns `0` | `1101 \| 1011 = 1111` (13 | 11 = 15) |
| XOR          | `^`        | Compares each bit and returns `1` if only one of the bits is `1`, otherwise return `0` | `1101 ^ 1011 = 0110` (13 ^ 11 = 6) |
| NOT          | `~`        | Inverts the bits - flips `1` to `0` and `0` to `1` | `~1101 = -1110` (two’s complement, ~13 = -14) |
| Left Shift   | `<<`       | Shifts bits to the left by the specified number of positions  | `0011 << 2 = 1100` (3 << 2 = 12) |
| Right Shift  | `>>`       | Shifts bits to the right by the specified number of positions | `1100 >> 2 = 0011` (12 >> 2 = 3) |

This seems like a lot and a little confusing, but let's break it down with some examples.

### AND (`&`)

The AND operator compares each bit of two numbers and returns `1` if both bits are `1`, otherwise it returns `0`. But what does that even mean? Let's take a look at an example:

```python
binary_1 = '1101' # Binary for decimal 13
binary_2 = '1011' # Binary for decimal 11
result = a & b # Perform bitwise AND operation
print(bin(result)) # Output: '0b1001'
```

The AND operator compares each bit of `binary_1` and `binary_2`. It might be easier to see if we line up the bits of the binary numbers:

```plaintext
1101 (13)
1011 (11)
```

Now we can compare each bit. If both bits are `1`, we get `1`, otherwise we get `0`:

```plaintext
1101 (13)
1011 (11)
----
1001 (9)
```

- First bit: `1 & 1 = 1`
- Second bit: `1 & 0 = 0`
- Third bit: `0 & 1 = 0`
- Fourth bit: `1 & 1 = 1`

So the result of `1101 & 1011` is `1001` or `9` in decimal.

### OR (`|`), XOR (`^`), and NOT (`~`)

Now that we have seen the AND operator in action we can apply those learnings to the bitwise operations. Let's see them in action:

```python
binary_1 = '1101' # Binary for decimal 13
binary_2 = '1011' # Binary for decimal 11

result_or = int(binary_1, 2) | int(binary_2, 2) # Perform bitwise OR operation
result_xor = int(binary_1, 2) ^ int(binary_2, 2) # Perform bitwise XOR operation
result_not = ~int(binary_1, 2) # Perform bitwise NOT operation

print(bin(result_or)) # Output: '0b1111'
print(bin(result_xor)) # Output: '0b110'
print(bin(result_not)) # Output: '-0b1110'
```

### Left Shift (`<<`) and Right Shift (`>>`)

The left shift operator (`<<`) shifts the bits of a number to the left by a specified number of positions. The right shift operator (`>>`) shifts the bits of a number to the right by a specified number of positions.

```python
binary_1 = '0011' # Binary for decimal 3

result_left_shift = int(binary_1, 2) << 2 # Shift bits to the left by 2 positions
result_right_shift = int(binary_1, 2) >> 1 # Shift bits to the right by 1 position

print(bin(result_left_shift)) # Output: '0b1100'
print(bin(result_right_shift)) # Output: '0b1'
```

While we might not need to use bitwise operators on a daily basis, it's good to know that they exist and how they work. They are often used in low-level programming, cryptography, and other specialized fields.

## Applications of Binary in Python

Now that we have a solid understanding of binary numbers and bitwise operators, let's explore some practical applications of binary in Python.

- **Binary File Handling in Python**: Using `open()` in binary mode.
- **Practical Use Cases**: Working with binary data and encryption basics.

