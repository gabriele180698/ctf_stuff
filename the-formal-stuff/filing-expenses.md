---
cover: >-
  https://images.unsplash.com/photo-1526304640581-d334cdbbf45e?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
description: >-
  This is a base mockup for an unpacking routine. It is useful when we have to
  deal with a packed challenge.
---

# Unpacking

{% hint style="info" %}
The packing keys can be taken from the original binary performing static and dynamic analysis.&#x20;
{% endhint %}

```python
import sys
from pwn import u32, p32

# check on the number of arguments
if len(sys.argv) < 4:
    print("usage: %s <inputfile> <address> <size>" % sys.argv[0])

filepath = sys.argv[1]
address = int(sys.argv[2], 16)
size = int(sys.argv[3], 16)

# start address of the binary
BEG_BIN = 0x00000000
# packing keys
KEY = [0x04030201, 0x40302010, 0x42303042, 0x44414544, 0xffffffff]

# load the binary
ff = open(filepath, "rb")
f = ff.read()
ff.close()

# compute the offset of the function(s) to unpack
off = address - BEG_BIN
# take the part of the binary to unpack
to_decode = f[off: off+(size*4)]
# this is an example of criterion for the keys
k = KEY[address % 5]

decode = b''

# example of unpacking algorithm
for i in range(size):
    decode += p32(u32(to_decode[i*4 : (i+1)*4]) ^ k)

# assemble the new binary
f = f[:off] + decode + f[off+(size*4):]

# write the new binary in a file
ff = open(filepath, "wb")
ff.write(f)
ff.close()
```
