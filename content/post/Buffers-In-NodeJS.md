+++
date = "2017-01-15T00:29:55+05:30"
title = "Buffers In NodeJS"
author = "Ankit Singh"
+++


Javascript works fine with strings and on their various operations but what about binary data consisting of bytes in which each byte is collection of 8bits that too in form of 0/1 ...It can't help much so node's buffer are here to your rescue.
As all data in our computer is present in form of bytes , low-level operations like reading a file or working with sockets can't be done alone with JS so.. Buffers are defined as container for raw bytes and it looks something like this..

\<Buffer 02 04 06 08 0a 0c 0e 10\>

Looks weird so lets dive in what above stuff actually is :-
  - Buffer :- a buffer has an Object type of Buffer.
  - Size:- Above is a size 8 buffer as it has 8 pairs of weird stuff and each        pair is a byte.

Hey , did i said wrong that byte are collection of 8bits then why above byte has 2 bits rather than 8 so lets see what it is actually ..

No - 2  Binary - 0001100  Hexadecimal - 0C
So Smart Node Devs thought that why not save some space and adopt hexa form which takes less bits than Binary thats why above Buffer object had 2 bits instead of 8.

### Encoding In Buffer
Code :
```sh
const buf = Buffer.from([0x68, 0x65, 0x6c, 0x6c, 0x6f, 0x20, 0x77, 0x6f, 0x72,
 0x6c, 0x64]);
 /*converts the array into a Buffer object .So it reads hey create a buffer from this array and return to buf constant.*/

console.log(buf);
// outputs <Buffer 68 65 6c 6c 6f 20 77 6f 72 6c 64>

console.log(buf.toString('utf8'));
// outputs 'hello world'
```
Various Commonly Used Encoding Types:-
  - UTF-8 - Includes ASCII's (0-127) characters along with its own set and all start with 1 to avoid clashing with ASCII.
  - UTF-16 -Capable of encoding all Unicode character and encoding is of variable lenght rest google it fella :)

So selecting the type of encoding can be like north and south when specially working with buffers along with other stuff.

In Above Example :
```sh
console.log(buff.toString('utf16le'));
//outputs '敨汬⁯潷汲'
```
Encoding is a Bi-directional process thus converting a string to buffer and vice-versa.

> Conceptually buffers are quite similar to arrays. They use bracket indexing and assignment just like arrays, and they have a length property as well as a concat and a slice method that works in basically the same way as arrays. However unlike javascript arrays, javascript buffers have a fixed length.

To Explore more kindly refer to the awesome [Node.js](https://nodejs.org/api/buffer.html) docs.
