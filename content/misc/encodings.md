+++
chapter = false
title = "Encodings"
weight = 5
+++


## Unicode
[Unicode](https://en.wikipedia.org/wiki/Unicode) is a **Standard**, not an Encoding
Standard for consistent encoding, representation and handling

- Maintained by Unicode Consortium
- consists of more than 140'000 graphic characters, 160 format characters
- covers more than 150 modern and historic scripts, multiple symbol sets and emojis

## UTF-8
UTF-8 is a variable-width character encoding. Defined by the Unicode standard.

## Base64
[Base64](https://en.wikipedia.org/wiki/Base64) is a group of binary-to-text
encoding schemes. Represents binary data in ASCII string format

## Fixed vs Variable Byte encodings
**fixed**
4 bytes | 4 bytes | 4 bytes | 4 bytes | 4 bytes 
**variable**
2 bytes | 2 bytes | 3 bytes | 1 bytes | 4 bytes 
works with prefix codes, declaring the length

continuation bit 0, end bit 1. packets of size n, starting with
either continuation or end bit. either it is the last packet or not.

100000110010101
0'0000001 0'0000011 1'0010101

100101100110011100100100000
0'0100101 0'1001100 0'1110010 1'0100000

111001001011001110
0'0001110 0'0100101 1'1001110


## Gamma Encoding
**Unary code**
12 --> 1111'1111'11110 (zero to terminate)
**Gamma code**
1. convert to zero
2. get rid of leading 1
3. determine length
4. write length in unary code
5. concat 'length in unary code' with 'binary without leading 1'

properties of gamma encoding:
- variable length encoding
- prefix encoding
- universal encoding
some good propery in light of shannon entropy

decimal --> binary --> no leading 1 --> unary of length
111222 --> 11011001001110110 --> 1011'0010'0111'0110 --> 1111'1111'1111'1111'0
 --> 1111'1111'1111'1111'0
89603 --> 10101111000000011 --> 0101'1110'0000'0011 --> 1111'1111'1111'1111'0
 --> 1111'1111'1111'1111'0
93710 --> 10110111000001110 --> 0110'1110'0000'1110 --> 1111'1111'1111'1111'0
 --> 1111'1111'1111'1111'0

