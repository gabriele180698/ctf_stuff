---
coverY: 0
---

# Welcome!

## Useful commands, scripts, and anything else

### Python

#### Useful imports and file configurators

```python
#!/bin/env python3
from pwn import *
import time
```

#### Startup the process or connect remotely

Split the command line using tmux (e.g. the running program on the left hand side and gdb on the right hand side)

```python
context.terminal = ['tmux', 'splitw', '-h']
```

Start the local process

```python
r=process("./program")
```

Attach gdb

```python
gdb.attach(r, """ b *0x40022b """)
```

Define host and port for the remote connection

```python
HOST='hack.paperino.it'
PORT='xxxx'
```

Connect to destination defined above

```python
r=remote(HOST,PORT)
```

Send an input

```python
r.send(str)    
r.sendline(str)
```

Receive something

```python
f = r.recv()
f = r.recvuntil('something\n')
```

Stop execution until an input

```python
input('Insert something')
```

Wait (useful to avoid short reads)

```python
time.sleep(0.2)
```

Make the shell interactive at the end of the script

```python
r.interactive()
```

#### Packed and Unpacked

Only for 8 bytes long elements

```python
g = u64(g)  
g = p64(g)
```

Only for 4 bytes long elements

```python
g = u32(g)     
g = u32(g)
```

To adjust the length

```python
g = g.ljust(8, b'\x00')
```

#### Python syntactic sugar

To write a file

```python
f=open("sol", "wb")
f.write(b)
```

To read a file

```python
str=open('sol','r').read()
```
