-- Clone a disk using partclone
We can use this to clone large disk size with low usage to lower disk size
```
Target partition size(107375 MB) is smaller than source(1073742 MB). Use option -C to disable size checking(Dangerous).
Partclone fail, please check /var/log/partclone.log !
```
```
partclone.ext4 -b -d -C -s /dev/vdb -o /dev/vdc
```

- Required package: partclone, nc

- Clone partition cross server
+ On target server
```
nc -l 8999 | partclone.ext4 -r -d -o /dev/sdb1
```

+ On local server, run:
```
partclone.ext4 -c -d -s /dev/sda1 | nc 10.5.0.123 8999
```
