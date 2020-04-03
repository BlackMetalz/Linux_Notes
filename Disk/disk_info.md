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

- Or even better info

```
[root@SVR497L ~]# udevadm info --query=all --name=/dev/sda | grep -i serial
E: ID_SERIAL=ST4000NM0033-9ZM170_Z1ZBJ9P7
E: ID_SERIAL_SHORT=Z1ZBJ9P7
```
