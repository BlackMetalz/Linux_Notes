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

Note:
```
WARNING: --num-threads is deprecated, use --threads instead
WARNING: --max-time is deprecated, use --time instead
```

Example output:
```
sysbench 1.0.20 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 60
Initializing random number generator from current time


Initializing worker threads...

Threads started!

SQL statistics:
    queries performed:
        read:                            570374
        write:                           162962
        other:                           81481
        total:                           814817
    transactions:                        40740  (677.42 per sec.)
    queries:                             814817 (13548.68 per sec.)
    ignored errors:                      1      (0.02 per sec.)
    reconnects:                          0      (0.00 per sec.)

General statistics:
    total time:                          60.1376s
    total number of events:              40740

Latency (ms):
         min:                                    9.70
         avg:                                   88.48
         max:                                 1251.46
         95th percentile:                      272.27
         sum:                              3604522.08

Threads fairness:
    events (avg/stddev):           679.0000/7.14
    execution time (avg/stddev):   60.0754/0.02
```
