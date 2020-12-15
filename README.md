# Reverse Engineering - All-In-One
Depending whether you are working with Windows or Linux binary, simply choose the folder of the operating system you are dealing with.  What you'll typically find about the resources on my repositories is that they are categorized and organized by relevance and skill level.  Enjoy!

[Browse my GitHub](https://github.com/Kennyslaboratory?tab=repositories) for even more awesome hacking resources!

------------------

## Best Books
| # | Title | Description | Skill Level |
| --- | --- | --- | --- |
| 1 | [Hacking, The Art of Exploitation](https://www.amazon.com/Hacking-Art-Exploitation-Jon-Erickson/dp/1593271441) | Best books for absolute newbies. Takes you step-by-step through the fundamentals.| Beginner |
| 2 | [Practical Reverse Engineering](https://www.amazon.com/Practical-Reverse-Engineering-Reversing-Obfuscation/dp/1118787315) | Information is very well organized. Tons of code examples. | Beginner |
| 3 | [Reversing, Secrets of Reverse Engineering](https://www.amazon.com/Reversing-Secrets-Engineering-Eldad-Eilam/dp/0764574817) | Once you've mastered the basics. This book will help take you to the next level. | Intermediate |


## Best Video Tutorials
| # | Title | Description | Skill Level |
| --- | --- | --- | --- |
| 1 | [Reverse Engineering Basics](https://www.youtube.com/watch?v=a2EkORFcSZo) | Start here if you know nothing. Take plenty of notes. | Beginner |


## Best Challenges
| # | Title | Description | Skill Level |
| --- | --- | --- | --- |
| 1 | [Protostar Challenges](https://exploit-exercises.lains.space/protostar/stack0/) | Watch the challenge walkthroughs created by [Live Overflow](https://old.liveoverflow.com/binary_hacking/protostar/stack0.html) | Beginner |
| 2 | [PicoCTF](https://play.picoctf.org/practice?category=3&page=1) | Various CTFs designed by Google, including reverse engineering challenges.  Follow challenge walkthrough by [John Hammond](https://www.youtube.com/watch?v=uIkxsBgkpj8) | Beginner |

-----------------
# List of Memory Bugs
| Bug | Description |
| --- | --- |
| [Buffer_Overflow]() | Writing past the bounds of a buffer.  For example, writing to a buffer without an null byte (\x00) appended at the end, therefore the program doesn't know when to stop writing user input to memory. |
 [Dangling_Pointers]() | When a pointer is pointing to an area of memeory that has already been freed.  Also known as, [Use-After-Free](http://phrack.org/issues/57/9.html). |
| [Off-By-One_Error]() | Found in loops that append data to a buffer.  Not checking the last iteration of the loop can overwrite the least signifcant byte on the function's base pointer. |
| [Race_Condition]() | When threads are in use.  If two or more threads can access shared data and try to change it at the same time.  |
| [Format_String_Attack]() | If a function like printf() is used to print input from a user and a format string is not specified. |
| [Integer_Overflow]() | Integers have a maximum value in memory.  A signed int can only go as high as 2,147,483,647 for example.  Math that goes beyond that limit can overflow the integer, resuting in unexpected behavior. |
| [Weak_Encryption]() | Using weak Pseudo-random seeds, for example using time() to provide a cryptographical seed for encryption or rand() function.. |

-----------------
# The Big Picture
**`DON'T TRY TO MEMORIZE EVERYTHING!!!`**
Just focus on truely memorizing the techniques used to analyze, debug, and examine memory.  I've created this Github as a place for students to get a fast overview of Reverse Engineering and leave you with a bird's eye view of it.

## Important Coding Concepts
| Subject | Description |
| --- | --- |
| [Arrays]() | Arrays and buffers are the same thing.  They point to [adjacent](https://www.merriam-webster.com/dictionary/adjacent) data streams located in memory and end with a NULL byte. (\x00). |
| [Pointers]() | Pointers have [types](https://www.learnjavaonline.org/en/Variables_and_Types), just like variables.  Pointers are used to store a location of data in memory. |
| [Strings]() | Strings are pointers to character arrays.  Strings point to the beginning of an array/buffer in memory to be read by a function like scanf(). |
| [Typecasting]() | C/C++ is a Strongly Typed Language.  You need to use Typecasting to change the type of a variable or pointer.  Despite how the type was originally defined. |
| [Vectors]() | Vectors are similar to arrays expect that they are used to store Object References instead of values with primative data types. |
| [File Descriptors]() | A number that is used to refernece an open file. |
| [Streams]() | The interface we use for reading and writing data to files, sockets, stdout, etc. |
| [Structs (C)]() | Structs in C are variables that contain multiple other variables. |
| [Classes]() | Class is short for _Classify._ A class is a blueprint for creating objects during runtime. Objects are dynamic and only spawn during runtime. Classes and Object Oriented Programming _(OOP)_ were added in C++. |
| [Structs(C++)]() | Structs in C++ are the same as Classes except they are by default set to Public. |

## Primitive Data Types
| Subject | Description | Byte Size |
| --- | --- | --- |
| [Signed_Int]() | Stores a whole number. Numbers in C are defaultly signed. Meaning, they can be either positive or negative numbers. 32-bit signed integers max out at 2,147,483,647. | 4 |
| [Unsigned_Int]() | Stores a whole number. Numbers that are unsigned can only be positive.  This means there is no [Twos Compliment](https://www.youtube.com/watch?v=lKTsv6iVxV4) and the least significant bit is not reserved. 32-bit unsigned integers max out at 4,294,967,295. | 4 |
| [Long]() | Store a whole number.  A long is double the memory size of an int, 8-bytes in 32-bit machines.  Used when an Int isn't big enough to store a value. | 8 |
| [Short]() | Store a whole number.  A short is half the size of an Int. 2-Bytes in 32-bit machines or simply 16-Bits in size. | 2 |
| [Float]() | Stores numbers with decimal points.  4-Bytes in size on 32-Bit machines.  Used for values with 6 to 7 decimals. | 4 |
| [Double]() | Stores numbers with decimal points. 8-Bytes in size on 32-Bit machines.  Used for values with up to 15 decimals. | 8 |
| [Char]() | 2 Bytes in size.  Chars are used to contain letters such as ASCII values. Strings are considered char arrays. | 2 |
| [Boolean]() | Either a True or False.  1-Bit in size. | 1-bit |

## Endianness and Byte Ordering
| Subject | Description |
| --- | --- |
| [Big Endian]() | Bytes in there normal order. _"Most significant byte first"_  0x12345678 = \x12\x34\x56\x78 |
| [Little Endian]() | Bytes in there reverse order. _"Least significant byte first"_  0x12345678 = \x78\x56\x34\x12 |




