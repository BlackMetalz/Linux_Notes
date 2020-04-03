- Get disk serial or model or full disk parameters
```
hdparm -I /dev/sdx | grep Model # Get the fucking Model Number
hdparm -I /dev/sdx | grep Serial # get the fucking serial number
```
- Incase disk is raid, use this instead of haparm

```
smartctl -i /dev/sdx | grep 'Serial'
```

- Incase of disk RO:

```
lsblk --nodeps -o name,serial
```
