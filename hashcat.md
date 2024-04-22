# Hashcat quick reference

#### Hashcat general use
```
hashcat -m 500 -a 0 -o result.txt hash /usr/share/wordlists/rockyou.txt
```
#### Combining multiple wordlists
```
/usr/share/hashcat-utils/combinator.bin fruits.txt veggies.txt > recipes.txt
```
```
cat  fruits.txt veggies.txt > recipes.txt
```
#### Creating a wordlist
```
cewl -m 3 -w recipes.txt https://www.example.com/fruits
```
#### Using rules
```
hashcat -w 3 -a 0 -m 500 hash wordlist.txt -r special-rules.rule
```

`-w 3` : Show status as process


#### Common Hash modes
| Mode | Flag |
| -- | -- |
MD5 | `-m 0`
SHA1 | `-m 100`
md5crypt | `-m 500`
$1$ | `-m 500`

[Full list](https://hashcat.net/wiki/doku.php?id=example_hashes)
