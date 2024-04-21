# Hashcat quick reference

`hashcat -m 500 -a 0 -o result.txt hash.txt /usr/share/wordlists/rockyou.txt`

To combine wordlists
```
/usr/share/hashcat-utils/combinator.bin fruits.txt veggies.txt > menu.txt
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
