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
  #do something with $i, not that the command itself should be foreground
}

p=24
cat log | while read line
do
  run "$i" &
  background=( $(jobs -p) )
  if (( ${#background[@]} == p )); then
    wait -n # -n option is for waiting any background job to finish, otherwise until all jobs finish
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
rsync -avzh --bwlimit=20000 /path-to-src /path-to-des # -z compression
rsync -avzh --bwlimit=20000 --exclude={'*.txt','dir3','dir4'} /path-to-src /path-to-des
rsync -avzh --bwlimit=20000 --exclude-from 'exclude-list.txt' /path-to-src /path-to-des
scp -r -l 400000 /path-to-src /path-to-des # unit kbit
```

6. Check if file contain some string
```bash
if grep -q SomeString File; then
  # Do something
fi
```

7. Check if a subfolder contains a file
```bash
find */$subfolder -type d '!' -exec test -e "{}/$file" ';' -print
```

8. Get the information between two lines, and get certain column:
```bash
awk "/$line1/{f=1;next} /$line2/{f=0} f" $file > tmp
awk -F ' ' '/$line1/{f=1;next} /$line2/{f=0} f { print $2,$3}' $file > tmp
```

9. Delete the information between two lines: (-E ensure some regex pattern like \s)
```bash
sed -i -E "/$line1/,/$line2/{//!d}" $orb_file
```

10. Get occurance of a character in a file
```bash
grep -o $char $file | wc -l
```

11. Combine static lib:
```bash
libtool -static -o new.a old1.a old2.a
```

12. Match the line in A file that exist in B file:
```bash
grep -p $A $B
```

13. Split the string by '_':
```bash
string1=$(echo $string | cut -f1 -d_)
string2=$(echo $string | cut -f2 -d_)
```

14. Transfer data with bandwidth (unit KBytes/s) limit rsync:
```bash
rsync –bwlimit=10000 /path/to/source /path/to/dest/
```

15. long time running command stdout without buffering:
```bash
./command.sh:
for i in `seq 1 100`
do 
  echo 1
  sleep 1
done

$ sudo yum install expect
$ unbuffer ./command.sh | tee -a log # real-time print out of "1" and redirect to log file
```

16. mean value and standard deviation:
```bash
#! /bin/bash
mean=`awk '{ total += $1; count++ } END { print total/count }' $1`
echo $mean
awk -v M="$mean" '{ total += ($1-M)*($1-M); count++ } END { print sqrt(total/count) }' $1
```

17. tr: delete
```bash
tr -d '\n'
```

18. add a file before/after the first line of a file:
```bash
sed -i -e '1 e cat file1' file2
sed -i -e '1r file1' file2
sed -i -e "/$matchedstring/r file1' file2

# add extra newline, need perl rather than sed
perl -pe "s/$string/$&\n\n$sth/" -i file

# for all files recursively under a directory:
find . -name $file -exec sed -i -e '1 e cat file1' file2 {} \;
```

19. check certain file containing strings in a dir, -H print dir/file name:
```bash
find $dir -name $file -exec grep -H $string {} \;
```

20. delete the whole line:
```bash
sed -i 's/$string//g' $file # not work
sed -i '/$string/d' $file # work
```

21. bash script check
```bash
bash -n script.sh # check error of script
sh -x script.sh aaa #
```

22. if $var is (not) defined, substitute with string:
```bash
${var:-string}, ${var:+string}, ${var:=string}, ${var:?string}
```

23. match the string in $var:
```bash
${var%pattern} # shortest match, from left
${var%%pattern} # longest match, from left
${var#pattern} # shortest match, from right
${var##pattern} # longest match, from right
```

24. print only the next line of match
```bash
awk '/$var/{getline; print}' $file
```

25. delete first and last line:
```bash
sed -i '1d;$d' $file
```

26. check the recent modified file:
```bash
find . -type f -mtime -90 # in the 90 days
```

27. add text/line at the beginning of a file, or after a line.
```bash
sed -i '1i $sth' $file
sed -i '1i\\' $file # a blank line
sed -i '0,/^/s/^/\n\n\n/g' $file # three blank lines
# after
sed -i '/$pattern/a $sth' $file
```

28. sum of a column
```bash
... | paste -sd+ - | bc
```

29. remove ^M carriage return.
```bash
sed -i -e "s/\r//g" $file
```

30. copy files with the parent structure
```bash
find $source -name "$file" -exec cp --parents \{\} $target \;
```

31. get certain chars in each line:
```bash
$command | cut -c1-10
```

32. awk use other delimiter:
```bash
awk -F ' ' '{print $1"\t"$2}' $file
```

33. compress data except for some subfolders including folders start with .:
```bash
tar zcvf data.tar.gz --exclude="./\.*" --exclude="$subfolder" .
```

34. exit a for loop if any error in the script in the loop:
```bash
set -e
cat $file | while read line || [[ -n $line ]] # ptherwise omit the last line without termination
do
# some scripts
...
done
```

35. list folders
```bash
ls XX* # it will show all files inside XX1/1.txt XX1/2.txt XX2/1.txt XX2/2.txt
ls -d XX* # it correctly shows XX1 XX2
```

36. awk multiple spaces
```bash
awk -F '[[:space:]][[:space:]]+'
```
