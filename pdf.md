# Crack PDF password


```
pdf2john secret.pdf > hash.txt
```

```
cat hash.txt | cut -d ":" -f 2- > pdf_hash.txt
```

```
hashcat pdf_hash.txt -m 10700 -a 0 /usr/share/wordlists/rockyou.txt
```
```
hashcat pdf_hash.txt -m 10700 --show
```
