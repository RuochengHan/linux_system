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
$ sudo smartctl -a /dev/nvme0
# if not available
$ sudo smartctl -T permissive -s on /dev/sda
$ sudo smartctl -T permissive -a /dev/sda
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

$ vim ~/.bashrc (~/.bash_profile)
PS1='\[\033[1;36m\]\u\[\033[1;31m\]@\[\033[1;32m\]\h:\[\033[1;35m\]\w\[\033[1;31m\]\$\[\033[0m\] '
```
7. Problem with vim delete, add to ~/.vimrc in the end:
```bash
set backspace=indent,eol,start
```

8. check mainboard and ram:
```bash
sudo dmidecode -t baseboard
sudo dmidecode --type 17
``` 

9. Install atom, only 1.51.0 support CentOS 7:
```bash
https://github.com/atom/atom/releases/tag/v1.51.0
```
