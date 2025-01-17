# Wordlists

Path to rockyou.txt
```
/usr/share/wordlists/rockyou.txt
```
Scraping a site to build a wordlist
```
cewl -m 3 -w fruits.txt https://example.com/category/fruits
```
* `-m 3` minimum 3 characters length
Count how many entries are on a file
```
wc -l fruits.txt
```
Remove spaces between words but keep each word on each line. `-i` means to make updates directly on the fruits.txt file.
```
sed -i 's/ //g' fruits.txt
```
Replace spaces with _ (underscore) and create a new file fruits-underscore.txt
```
sed 's/ /_/g' fruits.txt > fruits-underscore.txt
```
Repace spaces with - (dash) and create a new file fruits-dash.txt
```
sed 's/ /-/g' fruits.txt > fruits-dash.txt
```
Combines multiple files into one file
```
/usr/share/hashcat-utils/combinator.bin fruits.txt veggies.txt > dinner.txt
```
Remove duplicates and create a new file. 
```
sort dinner.txt | uniq > dinner-clean.txt
```













