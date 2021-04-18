1. GLIBC problem: https://itbilu.com/linux/management/NymXRUieg.html
2. IO status: 
```bash
$ sudo yum install iotop sysstat
$ sudo iotop
$ iostat
```
3. nvme temperature: 
```bash 
$ sudo yum install nvme-cli
$ sudo nvme smart-log /dev/nvme0
```
