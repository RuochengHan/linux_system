1. GLIBC problem: https://itbilu.com/linux/management/NymXRUieg.html
2. I/O status: https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/iostat.html
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
