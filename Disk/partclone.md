- Clone a disk using partclone

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
