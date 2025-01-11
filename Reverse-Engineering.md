## Reverse Engineering

Installing musl on kali [here](https://github.com/GinberSnap/command-cheatsheet/blob/main/setting-up-kali.md#installing-musl)

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
