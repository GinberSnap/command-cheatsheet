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

### GDB

1. `chmod +x ./banana`
2. `gdb ./banana`
3. `disass main`
4. `break __libc_start_main`
5. `run`
6. `c`

```
disass
``` 
```
gef➤ info files
```
```
gef➤ break *0x980
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
