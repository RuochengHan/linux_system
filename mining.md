1. Set GPU0 to 140 Watts
```bash
$ sudo nvidia-smi -i 0 -pl 140
```
2. to allow modifying core/memory clock: set coolbit to 12, then reboot computer.
3. Chia folder:
```bash
~/.chia/
```
4. Chia remote GUI: https://github.com/Chia-Network/chia-blockchain/wiki/Connecting-the-UI-to-a-remote-daemon
5. Chia connect to peers:
```bash
$ chia show -a chia.spdns.eu:8444
$ chia show -a node-eu.chia.net:8444
$ chia show -a introducer-eu.chia.net:8444
```
