**mount /home through network**
```bash
sudo sshfs -o allow_other,nonempty michaelbishop@192.168.1.111:/home /home
```
***allow_other*** make sure that other users can use as well
***nonempty*** overwrite the current home, but recover once umounted.

