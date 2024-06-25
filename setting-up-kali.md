# Setting up Kali 

## Kali

1. Download [kali](https://www.kali.org/get-kali/#kali-virtual-machines) and unzip
2. Open Virtual Machine, instead of creating a new one.
3. Then select a unzipped file to start the machine. 

## Wordlists & Rules

```
sudo gzip -d /usr/share/wordlists/rockyou.txt.gz
```

```
sudo mv OneRuleToRuleThemAll.rule /usr/share/hashcat/rules/
```

## Installing GDB

```
sudo apt install gdb
```

## Installing GEF
```
wget -O ~/.gdbinit-gef.py -q https://gef.blah.cat/py
echo source ~/.gdbinit-gef.py >> ~/.gdbinit
```

## Installing VScode

```
sudo apt install ./code_1.88.1-12345_amd64.deb
```

## Installing musl

```
sudo apt install musl-tools
```

To verify installation
```
echo -e '#include <stdio.h>\nint main() { printf("Hello, musl-gcc\\n"); return 0; }' > hello_musl.c
musl-gcc hello_musl.c -o hello_musl
./hello_musl
```

