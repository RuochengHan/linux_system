1. Read line by line from a file
```bash
cat log | while read line
do
  something
done
```

2. Print special charaters in awk, e.g. `"`:
```bash
awk -F ' ' '{print $1"\x22"}' file.dat
```

3. Run command in parallel with fixed number of process `p`:
```bash
run () {
  local i=$(echo $1 | sed 's/\///')
  do something with $i
}

p=24
cat log | while read line
do
  run "$i" &
  background=( $(jobs -p) )
  if (( ${#background[@]} == p )); then
    wait -n
  fi
done

```

4. Remove the first character from the string:
```bash
name="${name:1}"
```

5. Use `rsync` to copy files with limited bandwidth
```bash
rsync --bwlimit=20000 -vvv /path-to-src /path-to-des
rsync --bwlimit=20000 -vvv -e 'ssh -p $port' name@domain:/path-to-src /path-to-des
```

6. Check if file contain some string
```bash
if grep -q SomeString "$File"; then
  # Do something
fi
```
