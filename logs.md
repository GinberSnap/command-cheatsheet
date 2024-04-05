# Log - grep, awk


Output the rows that contain banana
```
cat customers.log | grep -E banana
```
```
cat customers.log | grep -E 'soy milk'
```

Output the row that contain words with 'ber' in them
```
grep -E 'ber' customers.log
```

Count the rows that contain banana
```
cat customers.log | grep banana | wc -l
```

banana **OR** apple
```
cat customers.log | grep -E 'banana|apple'
```

banana **AND** ny
```
cat customers.log | grep -E banana | grep -E ny
```

Output everything
```
awk '{print $0}' customers.log
```

Output 2nd, 3rd, and 7th columns 
```
cat customers.log | awk -F ',' '{print $2 "\t" $3 "\t" $7}' 
```

Filter by the content of a specific columns
```
egrep 'ber' customers.log | awk -F ',' '{print $2 "\t" $4}'
```

Count how many rows that contain bar in any column
```
grep -E $ber customers.log | wc -l
```

Count how many rows that contain bar in the 4th column
```
awk -F',' '{print $4}' customers.log | grep -o '\<.*ber.*\>' | wc -l
```

List all items in the 5th column along with the number of times they appear.
```
awk -F ',' '{print $5}' customers.log | sort | uniq -c
```

Count how many times banana appers in the 5th column 
```
cat customers.log | grep 'banana' | awk -F ',' '{print $5}' | uniq -c
```

```
grep -E nancy customers.log | cut -d ' ' -f 10 | sort | uniq -c
```

Look into the 4th column and return any value that contain 'ber', then show the number of time it appears
```
awk -F ',' '{print $1 "\t" $4}' customers.log | grep -E '\<.*ber.*\>' | sort --ignore-case | uniq -c 
```

Count how many uniqu value in the first field. " " space is being used to separate field. 
```
cat access.log | cut -d " " -f 1 | sort | uniq -c | wc -l
```

Count how many 404 in any columns on the entire file. 404 is preceded by " . (double-quote and space. " 404)
```
grep -E '\" 404' access.log | wc -l 
```

A file use multiple different separaters. Output 1st column. 
```
awk -F '[, ]' '{print $1}' access.log
```

Look into the last field.
```
awk -F '[, ]' '{print $NF}' access.log
```

Count how many unique values are in a specific column. Example, 5th column.
```
awk -F " " '{print $5}' access.log | sort | wc -l
```

Get the rows that contains admin and SUCCESS, then Output the total of all value from the 5th column. 
```
awk '/admin/ && /UPLOAD/ {sum += $5} END {print sum} access.log
```

Display IP address
```
grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" auth.log
```

Output IP address and the number of time they appear and sort into 1st and 2nd column.
```
grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" access.log | sort | uniq -c | awk '{print $1 "\t" $2}'
```



