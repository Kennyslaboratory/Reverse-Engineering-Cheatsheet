# Memory Basics

## The Big Picture
| # | Subject | Description |
| --- | --- | --- |
| 1 | Arrays | Arrays and buffers are the same thing.  They point to [adjacent](https://www.merriam-webster.com/dictionary/adjacent) data streams located in memory and end with a NULL byte. (\x00). |
| 2 | Pointers | Pointers have [types](https://www.learnjavaonline.org/en/Variables_and_Types), just like variables.  Pointers are used to store to location of data in memory. |
| 3 | Strings | Strings are pointers to character arrays.  Strings point to the beginning of an array/buffer in memory to be read by a function like scanf(). |

## Numerical Value Types
| # | Subject | Description |
| --- | --- | --- |
| 1 | Signed | Numbers in C are defaultly signed. Meaning, they can be either positive or negative. 32-bit signed integers max out at 2,147,483,647.
| 2 | Unsigned | Numbers that are unsigned can only be positive.  This means there is no [Twos Compliment](https://www.youtube.com/watch?v=lKTsv6iVxV4) and the least significant bit is not reserved. 32-bit unsigned integers max out at 4,294,967,295.
| 3 | Long | ... |
| 4 | Short | ... |

## Endiannessness and Byte Ordering
| # | Subject | Description |
| --- | --- | --- |
| 1 | Big Endian | ... |
| 2 | Little Endian | ... |

## Common Memory Bugs
| # | Bug | Description |
| --- | --- | --- |
| 1 | Buffer Overflow | ... |
| 2 | Danguling Pointers | ... |
| 3 | Off-By-One Errors | ... |
| 4 | Race Conditions | ... |
| 5 | Uncontrolled Format Strings | ... |
| 6 | Integer Overflow | ... |
| 7 | Weak Encryption | Using weak Pseudo-random seeds, for example using time() to provide a cryptographical seed for encryption. |
