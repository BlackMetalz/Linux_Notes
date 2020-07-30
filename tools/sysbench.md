```
apt install sysbench
```

Command:
```
sysbench oltp_read_write --table-size=20000000 --db-driver=mysql --mysql-db=test --mysql-user=root --mysql-password=root prepare
sysbench oltp_read_write --table-size=20000000 --db-driver=mysql --mysql-db=test --mysql-user=root --mysql-password=root --max-time=60  --max-requests=0 --num-threads=60 run
sysbench oltp_read_write --table-size=20000000 --db-driver=mysql --mysql-db=test --mysql-user=root --mysql-password=root cleanup
```
