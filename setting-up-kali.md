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

## Installing VScode

```
sudo apt install ./code_1.88.1-12345_amd64.deb
```
