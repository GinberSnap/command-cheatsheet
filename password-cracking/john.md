# John

To crack MD5 Crypt that is min 10 and max 12 characters
```
john --format=md5crypt --min-length=10 --max-length=12 hash
```

Using Rules and set min and max characters
```
john hash --wordlist=/usr/share/wordlists/rockyou.txt  --rules=/usr/share/wordlists/OneRuleToRuleThemAll.rule --min-length=10 --max-length=12
```
To see the result
```
john hash --show 
```
OR output result in a file
```
john  --format=Raw-MD5 --fork=2 --wordlist=/usr/share/wordlists/rockyou.tx  hash.txt > result.txt
```
