```
apt install sysbench
```

Command:
```
sysbench oltp_read_write --table-size=20000000 --db-driver=mysql --mysql-db=test --mysql-user=root --mysql-password=root prepare
sysbench oltp_read_write --table-size=20000000 --db-driver=mysql --mysql-db=test --mysql-user=root --mysql-password=root --max-time=60  --max-requests=0 --num-threads=60 run
sysbench oltp_read_write --table-size=20000000 --db-driver=mysql --mysql-db=test --mysql-user=root --mysql-password=root cleanup
```

If you prefer mysql sock instead of password
```
sysbench oltp_read_write --table-size=200000 --db-driver=mysql --mysql-db=test --mysql-user=root --mysql-socket=/data/var/lib/mysql/mysql.sock prepare

sysbench oltp_read_write --table-size=200000 --db-driver=mysql --mysql-db=test --mysql-user=root  --mysql-socket=/data/var/lib/mysql/mysql.sock --max-time=60  --max-requests=0 --num-threads=60 run

sysbench oltp_read_write --table-size=200000 --db-driver=mysql --mysql-db=test --mysql-user=root --mysql-socket=/data/var/lib/mysql/mysql.sock cleanup
```
