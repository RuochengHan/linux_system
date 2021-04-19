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
4. check ssd total written
```bash
echo "GB Written: $(echo "scale=3; $(sudo /usr/sbin/smartctl -A /dev/sdc | grep "Total_LBAs_Written" | awk '{print $10}') * 512 / 1073741824" | bc | sed ':a;s/\B[0-9]\{3\}\>/,&/;ta')"
 ```
