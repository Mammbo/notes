
# Integer Types
 
- `char` is the most fundamental type in C (1 byte = 8 bits).
- **signed char** range: $-128 \to 127$ ($-2^7 \to 2^7-1$)
- **unsigned char** range: $0 \to 255$ ($0 \to 2^8-1$)

| Type | Signed range | Unsigned range |
| ---- | ------------ | -------------- |
| `char` (8 bits) | $-2^7 \to 2^7-1$ = -128 → 127 | $0 \to 2^8-1$ = 0 → 255 |
| `short` (16 bits) | $-2^{15} \to 2^{15}-1$ = -32,768 → 32,767 | $0 \to 2^{16}-1$ = 0 → 65,535 |
| `int` (32 bits) | $-2^{31} \to 2^{31}-1$ ≈ -2.1B → 2.1B | $0 \to 2^{32}-1$ ≈ 4.29B |
 ## Powers of 2 to memorize
 
| Power       | Value                                 | Name        |
| ----------- | ------------------------------------- | ----------- |
| $2^{10}$    | 1,024                                 | 1 Ki (kilo) |
| $2^{12}$    | 4,096                                 | 4 Ki        |
| $2^{16}$    | 65,536                                | 64 Ki       |
| $2^{20}$    | 1,048,576                             | 1 Mi (mega) |
| $2^{30}$    | ~1.07 billion                         | 1 Gi (giga) |
| $2^{32}$    | ~4.29 billion                         | 4 Gi        |

| Data type   | Bytes                                 | Bits    |
| ----------- | ------------------------------------- | ------- |
| `char`      | 1                                     | 8       |
| `short`     | 2                                     | 16      |
| `int`       | 4                                     | 32      |
| `long`      | 4 (Windows) / 8 (Linux, macOS 64-bit) | 32 / 64 |
| `long long` | 8                                     | 64      |
| `int32_t`   | 4                                     | 32      |
| `int64_t`   | 8                                     | 64      |
| `float`     | 4                                     | 32      |
| `double`    | 8                                     | 64      |

# Binary Numbers
 
Binary is **base 2**. Hexadecimal is **base 16** (one hex digit = exactly 4 bits, which is why hex is so convenient).
 
For explanation we'll pretend `int4_t` exists (it **does not**), a 4-bit integer.
 
## 4-bit table
 
| Binary | Hex | Unsigned | Signed (two's complement) |
| ------ | --- | -------- | ------------------------- |
| 0000   | 0x0 | 0        | 0                         |
| 0001   | 0x1 | 1        | 1                         |
| 0010   | 0x2 | 2        | 2                         |
| 0011   | 0x3 | 3        | 3                         |
| 0100   | 0x4 | 4        | 4                         |
| 0101   | 0x5 | 5        | 5                         |
| 0110   | 0x6 | 6        | 6                         |
| 0111   | 0x7 | 7        | **7** ← signed max        |
| 1000   | 0x8 | 8        | **-8** ← signed min       |
| 1001   | 0x9 | 9        | -7                        |
| 1010   | 0xA | 10       | -6                        |
| 1011   | 0xB | 11       | -5                        |
| 1100   | 0xC | 12       | -4                        |
| 1101   | 0xD | 13       | -3                        |
| 1110   | 0xE | 14       | -2                        |
| 1111   | 0xF | 15       | **-1**                    |
## Two's complement
 
Give the **MSB (most significant bit, the LEFTMOST bit)** a **negative weight**. Everything else is normal binary.
 
Example: `1011` (unsigned 11)
$$1 \cdot 2^3 + 0 \cdot 2^2 + 1 \cdot 2^1 + 1 \cdot 2^0 = 11$$
Negative weight on the MSB:
$$-1 \cdot 2^3 + 0 \cdot 2^2 + 1 \cdot 2^1 + 1 \cdot 2^0 = -8 + 2 + 1 = -5$$
 
**Why it works:** the leftmost bit has the biggest weight. All the bits to its right add up to at most one less than it ($4+2+1 = 7 < 8$). So if the MSB is set (worth $-8$), no combination of the other bits can pull the total back to zero or above, so every number with the MSB set is negative.

Quick negation trick
> $-x$ = `~x + 1` (flip all bits, add 1). E.g. 5 = `0101` → flip → `1010` → +1 → `1011` = -5 ✓


# Integer Literals
 
`int x = 'A';` is the same as `int x = 65;` (ASCII). Characters in single quotes **are integers** (type `int` in C), so you can do arithmetic on them:
 
```c
'a' + 1        // 'b'
c - '0'        // converts digit char '7' to int 7
c - 'a' + 'A'  // lowercase to uppercase
```
 
## Escape sequences
 
| Escape | Value | Meaning |
| ------ | ----- | ------- |
| `'\n'` | 10 | newline |
| `'\t'` | 9 | tab |
| `'\0'` | 0 | null character |
| `'\13'` | 11 | octal escape (up to 3 octal digits) |
| `'\x41'` | 65 | hex escape (`'A'`) |
 
- `'\0'` == 0 is the **null character**. C strings are terminated with it.
- `0` != `'0'`. The character `'0'` is **48** in ASCII.
# Expressions vs Statements
 
- **Statement:** a piece of code that *does* something (produces an effect). Ends with `;` or is a `{ }` block.
- **Expression:** a piece of code that has a **value** and a **type**. Statements are built out of expressions.

| Expression | Value | Type |
| ---------- | ----- | ---- |
| `7 + 1` | 8 | `int` |
| `3.14 + 2` | 5.14 | `double` (2 is promoted) |
| `a == b` | 1 or 0 | `int` |
| `foo()` | whatever `foo` returns | `foo`'s return type |
| `x = 5` | 5 | type of `x` |
 
- The C compiler has well-defined **promotion rules** ("usual arithmetic conversions"): mixing `int` and `double` promotes the `int` to `double`. Also, `char` and `short` are promoted to `int` before any arithmetic.
- Boolean expressions have type `int`: 1 for true, 0 for false. Any nonzero value counts as true.


# Bitwise Operations
converting from signed to unsigned keeps the bit pattern and vice versa.
 
```c
int main() {
    int x = 1;   // 0001
    int y = 2;   // 0010
    int z;
 
    z = x & y;   // AND  -> 0000 = 0
    z = x | y;   // OR   -> 0011 = 3
    z = x ^ y;   // XOR  -> 0011 = 3
    z = ~x;      // NOT  -> 1110 = -2 (signed)
}
```
 
| Op  | Symbol | Result bit is 1 when…     |
| --- | ------ | ------------------------- |
| AND | `&`    | **both** bits are 1       |
| OR  | \|     | **at least one** bit is 1 |
| XOR | `^`    | bits are **different**    |
| NOT | `~`    | flips every bit           |

XOR comes up a lot in algorithms, graphics, and bit processing (e.g. `x ^ x = 0`, `x ^ 0 = x`, finding the single non-duplicated element in an array).
 
`~x` on 1: flip `0...0001` → `1...1110` = -2. (Matches the negation trick: `~x = -x - 1`.)
## Bit shifting
 
- `<<` shift left, `>>` shift right. The right operand is how many places to shift.
```c
int x = 1;          // 0000...0001
int z = x << 1;     // 0000...0010 = 2
z = 1 << 3;         // 0000...1000 = 8
```
 
`
 Right-shifting negative numbers
`>>` on a negative signed int is implementation-defined. In practice it's an **arithmetic shift** (copies the sign bit in), so `-8 >> 1 = -4`. Unsigned values always shift in 0s.
# Binary Numbers!

binary numbers are base 2. 

for the purpose of explanation we are going to use int4_t WHICH DOES NOT EXIST
- add table of 0 --> 15 in decimal binary and hex for the unsigned version  and the signed version 
- to verify this use two complement notation.
	- take the MSB which is the right all of those that are 1 are negative, and we give that bit a negative weight just change the sign and compute for the value it corresponds to.
		- Ex: 11 
		- = 1 * 2^3 + 0 * 2^2  + 1 * 2^1 + 1 * 2^0
		- if we give that a negative weight 
		- = -1 * 2^3 + 0 * 2^2  + 1 * 2^1 + 1 * 2^0 = -5
	- the left is LSP
	- the reasoning behind why this works is because the right most digit is the biggest in the number, everything to the left can at most be one less than it.
- examine boundary numbers: review this because i am confused in explanations
- int x = 0xffffffff; --> 4 byte integer = -1
- int x = 42 if you mean hex number 42 prepend with 0x42
- x = 0x80000000; -> -2^31
- x = 0x7fffffff; this is the maximum positive number --> 2^31 - 1
- int x = 0xffffffff; --> 4 byte integer --> if theis were unsigned it would be 2^31 - 1
conversion from sign to usigned preserver bit values.

- base 16 --> hexa decimal


# Integer Literals:
- int x = 'A'; === int x = 65; ---> ascii table implementation. if you write that character in single quotes it will convert it to a number.

- representing single characters and tabs 
	- '\n' --> 10
	- '\t' ---> 9
	- and so on and so forth
	- SINGLE QUOTE ARE INTEGERS AND YOU CAN ADD AND DO THINGS WITH THEM.
	- Every expression in C has a value and a type, all these have int type.
	- you can put up to 3 numbers after back slash to get octal numbers '\13' ---> 11 in decimal. Octal lowkey useless.
	- it is super useful to express number 0 --> '\0' == 0
	- zero is a null character in ascii and in C 0 are used to terminate the ending, of string for example so we can use '\0'
	- 0 !== '0' ---> this equals 48 in the ascii lookup.

# Expressions vs Statements
- Statement: a piece of code that does something, typically ends with a ; or with { } --> c program that does something, they produce an effect.
- within statemetns there are pieces that have a type and a value which are types
- an expression could also be more complicated like an arithmitic expression  7 + 1 ---> value 8 type int.
- C compiler has a well defined set of rules for promotion
	- 3.14 + 2--> 5.14 by promoting 2 to a double and the type value result would be a doubel
- boolean expressions ---> a == b ---> this type is int --> value of 1 for true 0 for false
- another expression ccould be a function call --> foo() has a return value for example of type char and the value is whatever it return.

# Bitwise Operations:
	` int main() {
			 int x = 1;
			 int y = 2;
			 int z;
			z = x & y; ---> this is bit wise AND compares the bits of x an y and if they are the same copies it if they are the opposite does not copy it. so they return value of this would be 0.
	}`
bitwise OR = 1 --> if you have a one between two expressions it would be True/1.
z = ~ (negation)x; ---> you would take the bit of whatever x is and flip all the bits; in signed this would be -2;

bitwise  XOR; 
z = x ^ y; ---> they have to be different there can only be 1 1 not 2 etc. ---> come up a lot in algos and graphics and bit processing.


Bit shifting:
>> bit shift right or << bit shift left
	int x = 1;
	int z = x << 1;` ---> ifx were 000000......1
	x << 1:  move everything one place left. ---> the one is how many places you shift.
	z = 1 << 3; shifting the repersentation of 1 three places over ---> you would get 8 


# Bit Wise Operators: 
- Bit wise &: Compares if two values are the same and outputs that num, if not ouputs 0. so o and 0 == 0, 0  and 1 == 0  1 and 0 == 0, 1 and 1 == 1,
- or is the opposite if there is either or or both are 1 then output will be 1.

## Bit shift Left:
![[Screenshot 2026-10-03 at 3.03.10 PM.png]]


## Bit Shift Right:![[Screenshot 2026-10-03 at 3.03.36 PM.png]]

# Logical Operations: 
- if statements and conditionals are used to evalue if somethis is true or false
- using a single variable if the evaluation of it is positive or negative number it is true (it exits), if it is 0 it is false (it doesnt exist)
- logical AND = && 
- logical OR == ||

```C
if ( x > 3 && x << 15) { 
	// the expression above follows pemdas
}
// if the first part of the expression in logical AND is false it will not evaluate the right statement. 
// this is called short cricuit evalutaiton
// this is the same for logical or but the opposite, if the first one is true it will not evaluate the right statement.
```

# Assignment: 
```C 
{ 
int x; y;
x = 1; //this has a type and value, therefore this is both a type and an expression

y = x = 1; 
//assignment operator works by going from right --> left;
}
x <<= 1 // changes x
x << 1 // does not change x

```

## prefix and postfix operator
- shorthand for adding 1 to a var is ++ x, this is a post fix operator
```C
int y; 
x = 1;
y = x++; // this is a postfix operators, ++ is higher precenance so it gets evaluated first, but since it is postfix the value before inrement is used so the output of this is 
x = 2, 
y = 1

// some examples of unary prefix and postfix operators
f() // unary function operator

-2 // unary negative prefix operator
a[3] // postfix indexing operator
```
![[Lecture 6.pdf]]