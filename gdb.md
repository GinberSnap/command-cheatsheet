## GDB

### Install GDB
```
sudo apt install gdb
```

### Install GEF
```
wget -O ~/.gdbinit-gef.py -q https://gef.blah.cat/py
echo source ~/.gdbinit-gef.py >> ~/.gdbinit
```

* `info functions` - List functions
* `disass main` - Disassemble main
* `break main` - Set breakpoint
* `d` - Delete breakpoints
* `print/x $eax` - Evaluate value of the register %eax in hex.
* `/d` for decimal
* `/t` for binary
* `/o` for octal
* `/u` for unsigned decimal
