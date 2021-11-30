# GDB

## gdbinit

We can create a file containing some commands that are executed when gdb is started. It is useful to automatize some operations.

The command to start gdb with the gdbinit file defined by us is the following.

```
gdb -q -x ./gdbinit
```

Here is an example of the gdbinit file.

```
file executable_file_name

b *0xffffffff

commands 1
    silent
    print "%c", $al
    c
end

r
```
