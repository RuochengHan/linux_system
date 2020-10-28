1. Read line by line from a file
```bash
cat log | while read line
do
  something
done
```

2. Print special charaters in awk, e.g. ***"***:
```bash
awk -F ' ' '{print $1"\x22"}' file.dat
```
