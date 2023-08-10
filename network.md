1. if wget forbidden 403:
```bash
wget --user-agent="Mozilla" $url
```

2. if wget obtain wrong file like 'download?...'
```bash
wget -v --content-disposition --header 'Cookie: ...' $url
```
