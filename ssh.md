# SSH
## Putty: Getting Server refused our key Error
```bash
chmod g-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```
In /etc/ssh/sshd_config (ref. https://stackoverflow.com/questions/20864224/putty-getting-server-refused-our-key-error)
```bash
PubkeyAcceptedKeyTypes=+ssh-rsa
PubkeyAuthentication yes
AuthorizedKeysFile  .ssh/authorized_keys
```
Check /var/log/auth.log for detailed info, noticed that need to search for your hostname
