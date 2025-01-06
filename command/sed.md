### Insert line before last line
```
sed -i '$i\mount -t nfs 10.0.0.1:/storage3/es-c1-snapshot /backup/es-c1' /etc/rc.local
```

- **Result**: `tail /etc/rc.local`
``` 
mount -t nfs 10.0.0.1:/storage3/es-c1-snapshot /backup/es-c1
exit 0
```
