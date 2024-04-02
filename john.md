# John

```
john --show hash.txt
```

```
john --format=raw-sha256 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```



Output result in a file
```
john  --format=Raw-MD5 --fork=2 --wordlist=/usr/share/wordlists/rockyou.tx  hash.txt > result.txt
```
