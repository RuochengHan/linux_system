Delete all jobs belonging to the $USER:
```bash
squeue -u $USER | grep $num | awk '{print $1}' | xargs -n 1 scancel
```
$num is the first several number of all jobs
