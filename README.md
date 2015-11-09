# Bitwise Operators

Bitwise operators change the underlying makeup of integers to change their values. To understand what bitwise operators are and how to use them, you first need to know the inner-workings of an integer.

## Binary Crash-Course

In day-to-day life for humans, we use numbers in base-10, meaning numbers range from 0 to 9 before increasing to 10. Although you normally interact with integers in a base-10 format while programming, they are implemented in a base-2 format, and you can take advantage of this sometimes for some pretty neat results. 

Integers being a base-2 format means that numbers range from 0 to 1 before the number reaches 10. As a visual comparison, let's look at how this compares to our normal base-10 scheme:

Base-10 | Base-2
--- | ---
0 | 0
1 | 1
2 | 10
3 | 11
4 | 100
5 | 101
6 | 110
7 | 111
8 | 1000
9 | 1001
10 | 1010

Under the hood, each 0 or 1 accounts for one bit of memory. This explains the maximum and minimum values that integer types can have. For example, the 8 bit storage of an unsigned char means that the maximum value it can hold in base-2 is 11111111, which in base-10 is 255. 

## Operators

Now with an understanding of the inner-workings of integers we can look into the 5 bitwise operations at our disposal: AND, OR, XOR, Complement, and Shift.

### Bitwise AND

Bitwise AND operators compares the two given numbers and only keeps the bits that match on both. The bitwise AND operator uses the '&' token. Here's a couple examples of what happens when using it:

```
    Ex 1           Ex 2

  00101011       00101011
& 10001010     & 11110000
  --------       --------
  00001010       00100000
```

This operator is great for masking away bits you don't want, or checking to see if certain bits are set. In code, the bitwise AND operator is used like this:

```cpp
unsigned int number = 21; // 00010101
unsigned int mask   = 7;  // 00000111

number = (number & mask);

cout << number << endl;

// Output: 5

//   00010101 or 21 in decimal (number)
// & 00000111 or 7 in decimal (mask)
//   --------
//   00000101 or 5 in decimal
```

You can even shorten it by doing "&=", just like any other arithmetic operator:

```cpp
unsigned int number = 21; // 00010101
unsigned int mask   = 7;  // 00000111

number &= mask;

cout << number << endl;
```

A quick example of the bitwise AND operator is determining if an integer is odd or even:

```cpp
// Check if the last bit is a 1, meaning it's an odd number.
bool isOdd(unsigned int number)
{
  return number & 1;
}
```

### Bitwise OR

The bitwise OR operator compares the two numbers and only keeps the bits where either one or both bits are set. Bitwise OR operator uses '|' token. Here are a couple examples of what the bitwise OR can do:

```
    Ex 1           Ex 2
  00101011       00101011
| 10001010     | 11110000
  --------       --------
  10101011       11111011
```

This operator is commonly used for setting desired bits on a given number. In code, the bitwise OR operator is used like this:

```cpp
unsigned int number = 8; // 00001000
unsigned int or_set = 1; // 00000001

number = (number | or_set);

cout << number << endl;

// Output: 9

//   00001000 or 8 in decimal (number)
// | 00000001 or 1 in decimal (or_set)
//   --------
//   00001001 or 9 in decimal
```

Just like the bitwise AND, you can also shorten the syntax and use the '|=' operator:

```cpp
unsigned int number = 8; // 00001000
unsigned int or_set = 1; // 00000001

number |= or_set;

cout << number << endl;
```

### Bitwise XOR

The bitwise XOR (shortened from Exclusive OR) is very similar to the bitwise OR, but with one small change. Instead of keeping the bits when either or both bits match, the XOR keeps the bits that ONLY have one bit set. The bitwise XOR operator uses the '^' token. Here are a couple examples of the XOR in action:

```
    Ex 1           Ex 2
  00101011       00101011
^ 10001010     ^ 11110000
  --------       --------
  10100001       11011011
```

The XOR can be used to toggle bits back and forth between set and not set. In code, the bitwise XOR looks like this:

```cpp
unsigned int number = 8;   // 00001000
unsigned int xor_set = 15; // 00001111

number = (number ^ xor_set);

cout << number << endl;

// Output: 7

//   00001000 or 8 in decimal (number)
// ^ 00001111 or 15 in decimal (xor_set)
//   --------
//   00000111 or 7 in decimal
```

And like the bitwise AND and OR operators, the XOR can calso be shortened into the '^=' operator if needed:

```cpp
unsigned int number = 8;   // 00001000
unsigned int xor_set = 15; // 00001111

number ^= xor_set;

cout << number << endl;
```

### Bit Complement

The bitwise Complement makes a mirror image of the given number. It can be seen as syntactical sugar for using the XOR with the maximum value for the given type, which would flip every bit in the number. The bitwise Complement uses the '~' token, and acts upon one value instead of two like the others. Here are a couple examples of the bitwise Complement in action:

```
    Ex 1           Ex 2
~ 00101011     ~ 11110000
  --------       --------
  11010100       00001111
```

In code, the bitwise Complement looks like this:

```cpp
unsigned int number = 15; // 00001111

number = ~number;

cout << number << endl;

// Output: 

// ~00001111 or 15 in decimal (number)
//  --------
//  11110000 or 240 in decimal
```

### Bit Shift

The bit shift operator takes the bits from a given number, and moves the position of those bits either left or right by however many bits you want. If the amount you move the bits in a direction causes set bits to exceed the bounds of the number, those bits will be lost. The bit shift operator uses the '>>' token for shifting to the right, and the '<<' token for shifting to the left. Here are a couple of examples of the bit shift operator in action:

```
     Ex 1            Ex 2
   01100000        00100010
<< 2            >> 3
   --------        --------
   10000000        00000100
```

Bit shifting is usually used to move data around into a more usable location. Let's see what the bit shift operator looks like in code:

```cpp
unsigned int number = 17; // 00010001
unsigned int shift_amount = 2; 

number = (number >> shift_amount);

cout << number << endl;

// Output: 4

//    00010001 or 17 in decimal (number)
// >> 2        (shift_amount)
//    --------
//    00000100 or 4 in decimal
```

Like the other operators, you can also shorten the operation to a '>>=' or '<<=' if needed:

```cpp
unsigned int number = 17; // 00010001
unsigned int shift_amount = 2; 

number >>= shift_amount;

cout << number << endl;
```

## Real World Examples

### Check for Power of 2

For an example of the bitwise AND operator being used in real code, let's say we're writing a graphics program that requires textures to have it's dimensions be a power of 2 (some formats require this, such as PVRTC textures). Let's look at how this might be implemented with bitwise operators. 

First, we should check out what numbers we can expect, then see if we can deduce any easy answers from them. Here are some numbers we want as positives:

```
2 pow 0 = 1  or binary 00000001
2 pow 1 = 2  or binary 00000010
2 pow 2 = 4  or binary 00000100
2 pow 3 = 8  or binary 00001000
2 pow 4 = 16 or binary 00010000
...
```

A quick look at these numbers show that every power of 2 has only one bit set, so an answer with bitwise operators should be pretty easy! Let's look at 2 numbers in particular to see any patterns: 16 and 21. 

**16**

As we can see, only 1 bit is set for 16. What if we minus 1 from this number?

```
  00010000
- 1
  --------
  00001111
```

Looks like there are no matching bits once we minus one number. We could guess at this point that maybe we can use the bitwise AND operator to check if there are any collisions after minusing 1. If there is a collision, it's not a power of 2!

**21**

The number 21 has a few bits set in it, since it isn't a power of 2. What if we minus 1 from this number also?

```
  00010101
- 1
  --------
  00010100
```

There are collisions on a non-power of 2 number! So it looks like using the bitwise AND operator will work. Let's check out a function that puts this idea into action:

```cpp
bool isPowerOf2(unsigned int number)
{
  return !(number & (number - 1));
}
```

So to reiterate, we can see that we're doing a bitwise operator against the number itself, and the same number minus 1. We are then doing a logical NOT operator to reverse the result, since finding a collision returns true, when we want it to return false since that means it's not a power of 2.

Let's run this through some numbers and see what the results are:

Input | Result | Input | Result | Input | Result | Input | Result | Input | Result
--- | --- | --- | --- | --- | --- | --- | --- | --- | ---
0 | true | 5 | false | 10 | false | 15 | false | 20 | false
1 | true | 6 | false | 11 | false | 16 | true | 21 | false
2 | true | 7 | false | 12 | false | 17 | false | 22 | false
3 | false | 8 | true | 13 | false | 18 | false | 23 | false
4 | true | 9 | false | 14 | false | 19 | false | 24 | false

Looks like every power of 2 is coming out right, except for one exception: 0 isn't a power of 2, but since 0 doesn't have any collisions, it's coming out as true! Let's fix that by adding on a little bit of code:

```cpp
bool isPowerOf2(unsigned int number)
{
  return number && !(number & (number - 1));
}
```

Now that we're checking is the number is non-zero (we're treating _number_ as a boolean, which implicitly converts to a bool, and any non-zero int becomes true), we get the right results:

Input | Result | Input | Result | Input | Result | Input | Result | Input | Result
--- | --- | --- | --- | --- | --- | --- | --- | --- | ---
0 | false | 5 | false | 10 | false | 15 | false | 20 | false
1 | true | 6 | false | 11 | false | 16 | true | 21 | false
2 | true | 7 | false | 12 | false | 17 | false | 22 | false
3 | false | 8 | true | 13 | false | 18 | false | 23 | false
4 | true | 9 | false | 14 | false | 19 | false | 24 | false

### Find Next Power of 2

For an example of the bitwise OR and shift operators being used in real code, let's look at a similar example of being able to, given any unsigned number, find the next power of 2. This can be used in graphics programming to scale textures up to the next compatible dimensions. 

Let's take a look at the number 17 for an example:

```
Decimal:         17
Binary:          00010001
Next Power of 2: 00100000
```

As you can see above, the next power of two for 17 is just one to the left of it's left-most set bit. If we could set all the bits to the right of the left-most bit, and then add 1 to the number, we would be able to get the next power of 2! We can do this very easily with the bitwise OR and some bit shifting. 

```cpp
17 as binary is 00010001

   00010001   /--->  00001000   /--->  00011001   /--->  00000110   /--->  00011111
>> 1          |    | 00010001   |   >> 2          |    | 00011001   |    + 1
   --------   |      --------   |      --------   |      --------   |      --------
   00001000 --/      00011001 --/      00000110 --/      00011111 --/      00100000
```

So you just need to bitwise OR with the shifted value over and over again until all the bits to the right are set! An 8 bit unsigned char will need to be shifted and OR'd by the values 1, 2, and 4 to cover all the bits to the right of any value. For a 32 bit unsigned int, it will have to be shifted and OR'd by 1, 2, 4, 8, and 16. This can be shown in code like this:

```cpp
unsigned int nextPowerOf2(unsigned int number)
{
  // Set all bits to the right of the left-most bit
  // Ex. 00100100 -> 00111111
  number |= (number >> 1);
  number |= (number >> 2);
  number |= (number >> 4);
  number |= (number >> 8);
  number |= (number >> 16);
  
  // Add 1 to get the next power of 2
  // Ex. 00111111 -> 01000000
  number += 1;
  
  return number;
}
```

This code will then output this result:

Input | Result | Input | Result | Input | Result | Input | Result | Input | Result
--- | --- | --- | --- | --- | --- | --- | --- | --- | ---
0 | 1 | 5 | 8 | 10 | 16 | 15 | 16 | 20 | 32
1 | 2 | 6 | 8 | 11 | 16 | 16 | 32 | 21 | 32
2 | 4 | 7 | 8 | 12 | 16 | 17 | 32 | 22 | 32
3 | 4 | 8 | 16 | 13 | 16 | 18 | 32 | 23 | 32
4 | 8 | 9 | 16 | 14 | 16 | 19 | 32 | 24 | 32
