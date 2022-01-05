---
description: Returned Oriented Programming
---

# ROP

## Tools

### Ropper

This is a tool to search for gadgets inside an executable.&#x20;

#### Show all the gadgets

```bash
ropper -f elfpath
```

#### Search by regexp

```
ropper -f elfpath --search "regexp"
```

#### Save gadgets into a file

```
ropper --nocolor -f elfpath > gadgets.txt
```

### One Gadget

Tool to search for one gadgets (magic gadgets) into the libc. It returns also the condition that we must satisfy in order to obtain a shell with that specific one gadget.&#x20;

```
one_gadget path/libc-version.so
```
