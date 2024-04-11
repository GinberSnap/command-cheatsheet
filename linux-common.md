### Rockyou

- Path: `/usr/share/wordlists/rockyou.txt`
- Show wordlists directory" `ls -lh /usr/share/wordlists/`
- Open rockyou zip: `sudo gunzip /usr/share/wordlists/rockyou.txt.gz`

### Zlib

```
zlib-flate -uncompress < banana.pdf > banana_extracted
```

### Binwalk

```
binwalk -e customers.xlsx
```

```
binwalk --dd='.*' customers.xlsx
```

### Brotili

```
brotli -d banana.png -o banana_dec.png
```


### Check Checksum
```
wget -O- http://www.example.com:80/example.pdf | sha256sum
```


