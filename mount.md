**mount /home through network**
```bash
sudo sshfs michaelbishop@192.168.1.100:/home /home -o nonempty -o allow_other -o default_permissions -F /dev/null -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -o IdentitiesOnly=yes -o IdentityFile=/dev/null
```
***allow_other*** make sure that other users can use as well
***nonempty*** overwrite the current home, but recover once umounted.

Remeber to also create the same user.

**mount disk**
```bash
$ lsblk
$ mount /dev/sdc /scratch
$ sudo mkfs.ext4 /dev/sdc (format, if neccessary)
$ sudo mkfs -t ntfs /dev/sdf1 (format to ntfs e.g. for windows)
```
Other info: https://www.jianshu.com/p/d0c75fd8bcc5

remove the reserve space for superuser: https://askubuntu.com/questions/249387/df-h-used-space-avail-free-space-is-less-than-the-total-size-of-home
```bash
$ sudo tune2fs -l /dev/sdc # check
$ sudo tune2fs -m 0 /dev/sdc # set from 5 % to 0
# seems not work for ntfs

```
**mount remote Windows' harddisk to Linux** \
Need to set dir_mode and file_mode, otherwise is default rwx only for root
```bash
# pay attention to space in Windows username "\ "
sudo mount -t cifs //winIP/winfolder /mnt/win -o username=winsuer,dir_mode=0777,file_mode=0777
```
**mount ntfs (win) format**
Remember to select the correct partition, like /dev/sdf2 rather than /dev/sdf
```bash
mount -t ntfs-3g /dev/sdf2 /mnt/win
```
