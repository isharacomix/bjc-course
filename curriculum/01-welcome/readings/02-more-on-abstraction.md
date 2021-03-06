---
layout: page
title: More on Abstraction
unit: 1
uniturl: 01-welcome
reading: 2
readingurl: 02-more-on-abstraction
---


More on Abstraction
===================
This introduces the concept that *abstractions built upon binary sequences can
be used to represent all digital data*. It also introduces the idea the *computing
has global impacts*. It focuses, in part, on the following learning objectives:

 * 5: The student can describe the combination of abstractions used to represent data.
 * 6: The student can explain how binary sequences are used to represent digital data.
 * 28: The student can analyze how computing affects communication, interaction, and cognition.
 * 29: The student can connect computing with innovations in other fields.
 * 30: The student can analyze the beneficial and harmful effects of computing.
 * 31: The student can connect computing within economic, social, and cultural contexts.


Bits as the Natural Unit of Information
---------------------------------------
This was the seminal insight of [Claude Shannon](http://en.wikipedia.org/wiki/Claude_Shannon),
founder of information and communication theory. As this chapter illustrates all
information stored on computers (documents, photos, songs, etc.) and communicated
through the Internet (email, blogs, twitter posts, etc.) are represented as bits,
zeros and ones.

*Digital data* are represented in discrete *bits* (**B**inary dig**IT**s). Analog
data are represented as a continuous quantity. Think of the difference between a
digital watch that displays hours, minutes, seconds, and tenths of a second, and
an *analog clock*, with hour hand, minute hand, and a sweep second hand.

Think of the difference in *fidelity* between
[digital vs. analog recordings](http://www.howstuffworks.com/analog-digital3.htm).



Moore's Law
-----------
[Moore's law](http://en.wikipedia.org/wiki/Moore%27s_law) is the observation that
the number of transistors that could be packed onto a integrated circuit seemed
to double ever two years or so. This remarkable trend about
[exponential growth](http://en.wikipedia.org/wiki/File:Exponential.svg) in chip
density has proved to be true for 40 years now.

Someone offers you a summer job and offers you two payment schemes: (1) $10 per
hour for 40 hours per week for 30 days or (2) One cent on day 1, two cents and
day two, four cents on day three and on (doubling each day) for 30 days. Which
pay would you choose?
[Click here to see how exponential growth affects this question](http://www.cs.trincoll.edu/~ram/aitalk/twos.txt).



It's All Just Bits
------------------
**Binary digits (bits)** correspond naturally to electronic circuits where 1
represents 'on' and 0 represents 'off'. In computers, binary sequences are used
to represent all kinds of data: text, numbers, images, sounds, ..., everything.

Depending on the context, the same string of bits can represent different types
of information. These are all examples of **abstraction** at work:
 * The sequence ```0100 0001``` can represent the [binary numeral](http://en.wikipedia.org/wiki/Binary_numeral_system) for the decimal value 65 when it occurs calculator.
 * The sequence ```0100 0001``` can represent the [ASCII letter](http://www.ascii.cl/) 'A' when it occurs in an email message.
 * The sequence ```0100 0001``` can represent the amount of Red in the [RGB color model](http://en.wikipedia.org/wiki/RGB_color_model) when it occurs in an image.
 * The sequence ```0100 0001``` can represent the MOV B,C machine operation on the Intel [8080 8-bit processor](http://nemesis.lonestar.org/computers/tandy/software/apps/m4/qd/opcodes.html)



A Little Bit About Bits
-----------------------
A **byte** is an 8-bit sequence. Historially an 8-bit byte was used to represent
a single character in computer memory.

The length of a binary sequence -- a sequence of 0s and 1s -- determines the
number of different sequences that can be generated and therefore the number of
different things that can be represented by such a sequence.

For example, with 1 bit, you can have two different sequences, 0 or 1, which can
stand for two different colors, say, 0 stands for white and 1 for black. With 2
bits, you can have four different sequences, 00, 01, 10, or 11, which can represent
four different colors, white, black, red, green. And so on.

In general, an n-bit sequence can represent 2<sup>n</sup> different things.
Here's how:


| Number of Bits | Number of Things       | Representations                 |
|:--------------:|:----------------------:| ------------------------------- |
| 1              | 2 (ie 2<sup>1</sup>)   | 0,1                             |
| 2              | 4 (ie 2<sup>2</sup>)   | 00,01,10,11                     |
| 3              | 8 (ie 2<sup>3</sup>)   | 000,001,010,011,100,101,110,111 |
| 4              | 16 (ie 2<sup>4</sup>)  |                                 |
| 5              | 32 (ie 2<sup>5</sup>)  |                                 |
| 6              | 64 (ie 2<sup>6</sup>)  |                                 |
| 7              | 128 (ie 2<sup>7</sup>) |                                 |
| 8              | 256 (ie 2<sup>8</sup>) |                                 |



Data Abstraction: How Colors Are Represented in Bits
----------------------------------------------------
<img src="rgb.png" align="right" width="250" />

The [RGB model](http://en.wikipedia.org/wiki/RGB_color_model) adds together 3
primary colors, Red, Green, and Blue, where each color component (R,G,B) is
represented as an 8-bit **byte**.

If there are 256 (2<sup>8</sup>) possible values for each of R,G,B, the triplet
can represent 256 × 256 × 256 = 16,777,216 different colors, which corresponds
well to the number of colors the human eye can distinguish.

 * (R, G, B)
 * (65,65,65) = Grey
 * (255,0,0) = Red
 * (0,255,0) = Green
 * (0,0,255) = Blue
 * (65,0,0) = Brown
 
Try to mix your own colors: [Colorschemer.com](http://www.colorschemer.com/online.html)


Perfection is Normal
--------------------
Because they are based on strings of discrete bits, *digital* (as opposed to
*analog*) copies are perfect copies.

Computer scientists and engineers have developed effective
[error detection](http://en.wikipedia.org/wiki/Parity_bit) and error correction
schemes to insure accurate data representation and communication.


Example: Parity Bit Error Detection
-----------------------------------
Suppose you are sending a stream of data to a server. By adding a parity bit,
you enable to the server to detect some basic transmission errors. For example,
if the server expects that every byte will contain an **even number of 1s** and
it detects a byte such as ```0001 0101``` with an odd number of 1s, it can tell
that an error occured. Perhaps the user meant to send ```0000 0101``` but one of
the bits was flipped from 0 to 1 during transmission.

A **parity bit** is a bit that is added as the leftmost bit of a bit string to
ensure that the number of bits that are 1 in the bit string are even or odd.

To see how this works, suppose our data are stored in strings containing 7 bits.

In an **even parity scheme** the eighth bit, the parity bit, is set to 1 if the
number of 1s in the 7 data bits is odd, thereby making the number of 1s in the
8-bit byte an even number. It is set to 0 if the number of 1s in the data is even.

In an **odd parity scheme** the eighth bit, the parity bit, is set to 1 if the
number of 1s in the 7 data bits is even, thereby making the number of 1s in the
8-bit byte an odd number. It is set to 0 if the number of 1s in the data is odd.

The following table summarize this approach.

| Data Bits (7)         | Even Parity (even number 1s) | Odd Parity (odd number 1s) |
| --------------------- | ---------------------------- | -------------------------- |
| ```000 0000``` (0 1s) | ```0000 0000```              | ```1000 0000```            | 
| ```011 0010``` (3 1s) | ```1011 0010```              | ```0011 0010```            | 
| ```011 0011``` (4 1s) | ```0011 0011```              | ```1011 0011```            | 
| ```011 0111``` (5 1s) | ```1011 0111```              | ```0011 0111```            | 


Question: What would happen in this scheme if 2 bits were switched from 1 to 0
or 0 to 1?


Quiz Yourself
-------------
To see if you understand these concepts, try the following quizzes. If you can
get ten-in-a-row correct, that's a pretty good indication that you get it.

 * [Parity Error Detection I](http://www.cs.trincoll.edu/%7Eram/q/110/parity-error-detection.html)
 * [Parity Error Detection II](http://www.cs.trincoll.edu/%7Eram/q/110/parity-error-detection-2.html)


Variables and Abstraction
-------------------------
When you program you will create variables to make the script much more
functional -- i.e., the user could change the value of the variable.

This is an important example of **abstraction** at work -- in this case, we are
letting an *abstract symbol* (the variable) represent or stand for something
else (its value, 2 or 8). 



What is a Variable?
-------------------
A *variable* in a computer program is a *symbol* that represents a *memory
location* where a piece of data can be stored. You can think of a computer memory
as a large array of numbered mail boxes, where the numbers represent the address
of the memory location. In this example, there are 8 memory locations numbered
17-24 (in decimal) and 10001 - 11000 (in binary). None of the locations have any
value stored in them yet.

| 17    | 18    | 19    | 20    | 21    | 22    | 23    | 24    |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 10001 | 10010 | 10011 | 10100 | 10101 | 10110 | 10111 | 11000 |
|       |       |       |       |       |       |       |       |

When you define a *variable*, you are giving name to a memory location.

| name  | score | wins  | 20    | 21    | 22    | 23    | 24    |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 10001 | 10010 | 10011 | 10100 | 10101 | 10110 | 10111 | 11000 |
| Joe   | 8     | 2     |       |       |       |       |       |


What is a Value?
----------------

In a computer program a *value* is a symbol of a piece of *data*. For example,
the numeral '8' represents the number 8. Values (data) are stored in the
computer's memory locations.

Symbols like the numeral '8' are also examples of *abstractions*. The numeral
'8' and the word 'eight' and the binary string '1000' are all symbols that
represent the number 8, which is itself an abstract concept of 8 things. For
example, they can all be used to refer to the number of little circles here:
o o o o o o o o.

So, in a computer program we use abstract symbols to represent both *variables*
and *values*.


Values vs. Variables
--------------------
It's important to distinguish between the variable's *name* (e.g., score or name)
from the *value* that it represents -- i.e, from the value that it is storing in
its memory location (e.g., **8** or **Joe**).


*Material from Dr. Ralph Morelli, Trinity College*


