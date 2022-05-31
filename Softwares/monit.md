1. Install `monit` pkg

2. Create following folder, in this example I'm gonna using `hbase` user to use monit for thrift port

```
/home/hbase/.monitrc
/home/hbase/.monit.d
/home/hbase/.monit/events
/home/hbase/.monit/log
```


3. Change user to hbase, start monit process by `monit`

4. Start specific Process. Ex `thrift`

create new file in `~/.monit.d/thrift` with following content:
```
check process thrift with pidfile /tmp/hbase-hbase-thrift.pid
   start program = "/opt/softs/hbase/bin/hbase-daemon.sh start thrift"
   stop  program = "/opt/softs/hbase/bin/hbase-daemon.sh stop thrift"
   group hbase-thrift
```

after that start thrift process by: monit start process

5. Check result with: `monit status`
Output demo: 

```
Monit 5.26.0 uptime: 0m

Process 'thrift'
  status                       OK
  monitoring status            Monitored
  monitoring mode              active
  on reboot                    start
  pid                          1511829
  parent pid                   1511812
  uid                          1000
  effective uid                1000
  gid                          1000
  uptime                       0m
  threads                      39
  children                     0
  cpu                          1.2%
  cpu total                    1.2%
  memory                       0.2% [61.5 MB]
  memory total                 0.2% [61.5 MB]
  security attribute           unconfined
  disk read                    0 B/s [20.7 MB total]
  disk write                   0 B/s [112 kB total]
  data collected               Tue, 31 May 2022 16:27:06
```
