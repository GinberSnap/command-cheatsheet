# Hashcat quick reference

#### Hashcat general use

To crack MD5 `-m 0` using rockyou.txt
```
hashcat -m 0 -a 0 -o cracked.txt hash.txt /usr/share/wordlists/rockyou.txt
```
To crack SHA1 `-m 100` 
```
hashcat -m 0 -a 0 -o cracked.txt hash.txt /usr/share/wordlists/rockyou.txt
```
To crack MD5 that starts with CTF-ABCD-, followed by 4 digits.
```
hashcat -m 0 -a 3 hash CTF-ABCD-?d?d?d?d
```

To crack MD5 that is min 8 and max 10 characters. 
```
hashcat -m 500 -a 3 -o cracked.txt hash.txt /usr/share/wordlists/rockyou.txt --increment --increment-min=8 --increment-max=10
```

[Hashcat Modes](https://hashcat.net/wiki/doku.php?id=example_hashes), [Man page](https://hashcat.net/wiki/doku.php?id=hashcat), [Hashcat Mask](https://hashcat.net/wiki/doku.php?id=mask_attack)

#### Attack modes
* `-a 0`: Straight (simple wordlist attack)
* `-a 1`: Combination (combines words from two wordlists)
* `-a 3`: Brute-force (all possible combinations based on mask)
* `-a 6`: Hybrid wordlist + mask (wordlist + mask attack)
* `-a 7`: Hybrid mask + wordlist (mask + wordlist attack)
* `-a 0 --rules-file`: Dictionary + **Rule based** Mode

**Rules**
```
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --rules-file /usr/share/wordlists/OneRuleToRuleThemAll.rule
```

#### Example Mask Syntax (-a 3 and -a 6, -a 7):

* `?l`: Lowercase letter (a-z)
* `?u`: Uppercase letter (A-Z)
* `?d`: Digit (0-9)
* `?s`: Special character (e.g., !, @, #)
* `?b`: Space or control character
* `?a`: Any character (lowercase, uppercase, digit, special character)


### Use Hashcat on Windows
```
cd hashcat

hashcat.ext -m 0 -a 0 c:\User\Desktop\hashcat\hash.txt c:\User\Desktop\hashcat\wordlists\rockyou.txt
```
Mask - `-a 6` is hybrid mode. 
```
hashcat.ext -m 0 -a 6 c:\User\Desktop\hashcat\hash.txt c:\User\Desktop\hashcat\wordlists\rockyou.txt  ?d?d?d
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
hashcat -w 3 -a 0 -m 500 hash wordlist.txt -r OneRuleToRuleThemStill.rule
```
```
hashcat -w 3 -a 0 -m 500 hash wordlist.txt -r OneRuleToRuleThem.rule
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
