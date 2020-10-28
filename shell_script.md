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
