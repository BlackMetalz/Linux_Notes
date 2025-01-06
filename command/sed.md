### Insert line before last line
```
sed -i '$i\mount -t nfs 10.0.0.1:/storage3/es-c1-snapshot /backup/es-c1' /etc/rc.local
```

- **Result**: `tail /etc/rc.local`
``` 
mount -t nfs 10.0.0.1:/storage3/es-c1-snapshot /backup/es-c1
exit 0
```
- **Real example for change snapshot path in Elasticsearch in an automation way xD**:
```
systemctl stop elasticsearch && sed -i 's/snapshots/backup/g' /etc/elasticsearch/elasticsearch.yml
umount /snapshots && mkdir -p /backup/es-c1 && mount -t nfs 10.0.0.1:/storage3/es-c1-snapshot /backup/es-c1 && chown -R elasticsearch:elasticsearch /backup/es-c1
sed -i '$i\mount -t nfs 10.0.0.1:/storage3/es-c1-snapshot /backup/es-c1' /etc/rc.local
service elasticsearch start
```
