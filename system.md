1. GLIBC problem: https://itbilu.com/linux/management/NymXRUieg.html
2. I/O status: https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/iostat.html
```bash
$ sudo yum install iotop sysstat dstat
$ sudo iotop # this only show total I/O
$ iostat # this show the value from CPU
$ dstat -tdD total,sda,sdb,sdc # this is better, show directly from every disk
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
5. check the port using PID:
```bash
$ sudo lsof -i -P -n | grep $port
```
6. color scheme used:
```bash
$ vim ~/.vimrc
syntax on
colorscheme evening

$ vim ~/.bashrc
PS1='\[\033[1;36m\]\u\[\033[1;31m\]@\[\033[1;32m\]\h:\[\033[1;35m\]\w\[\033[1;31m\]\$\[\033[0m\] '
```
