**mount /home through network**
```bash
sudo sshfs michaelbishop@192.168.1.100:/home /home -o nonempty -o allow_other -o default_permissions -F /dev/null -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -o IdentitiesOnly=yes -o IdentityFile=/dev/null
```
***allow_other*** make sure that other users can use as well
***nonempty*** overwrite the current home, but recover once umounted.

Remeber to also create the same user.
