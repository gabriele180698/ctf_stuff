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

#### Save gadgtes into a file

```
ropper --nocolor -f elfpath > gadgets.txt
```
