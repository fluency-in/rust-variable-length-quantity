# Rust: Variable Length Quantity

Implement variable length quantity encoding and decoding.

The goal of this exercise is to implement [VLQ](https://en.wikipedia.org/wiki/Variable-length_quantity) encoding/decoding.

In short, the goal of this encoding is to encode integer values in a way that would save bytes.
Only the first 7 bits of each byte is significant (right-justified; sort of like an ASCII byte). 
So, if you have a 32-bit value, you have to unpack it into a series of 7-bit bytes. 
Of course, you will have a variable number of bytes depending upon your integer. 
To indicate which is the last byte of the series, you leave bit #7 clear.
In all of the preceding bytes, you set bit #7. 

So, if an integer is between `0-127`, it can be represented as one byte. 
The largest integer allowed is `0FFFFFFF`, which translates to 4 bytes variable length. 
Here are examples of delta-times as 32-bit values, and the variable length quantities that they translate to:


```
 NUMBER        VARIABLE QUANTITY
00000000              00
00000040              40
0000007F              7F
00000080             81 00
00002000             C0 00
00003FFF             FF 7F
00004000           81 80 00
00100000           C0 80 00
001FFFFF           FF FF 7F
00200000          81 80 80 00
08000000          C0 80 80 00
0FFFFFFF          FF FF FF 7F
```

Follow the instructions [here][rust-testing] to run the tests.

[rust-testing]: https://github.com/exercism/xrust/blob/master/docs/TESTS.md

## Source

A poor Splice developer having to implement MIDI encoding/decoding. [https://splice.com](https://splice.com)

This exercise is from the [Rust][rust] track on [Exercism][exercism]

[exercism]: http://exercism.io
[rust]: http://exercism.io/languages/rust



