# Example: https://www.tecmint.com/10-lsof-command-examples-in-linux/

- file deleted file but not give free space

```
lsof | grep deleted
```

- Find which process used to open: # https://developer.ibm.com/tutorials/l-lpic1-104-3/
```
[root@attic4‑cent ~]#umount /dos
umount: /dos: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
[root@attic4‑cent ~]#lsof ‑w /dos
COMMAND     PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
slowread. 28960  ian    0r   REG    8,3     1207    2 /dos/fstab
sleep     28972  ian    0r   REG    8,3     1207    2 /dos/fstab
``` 
