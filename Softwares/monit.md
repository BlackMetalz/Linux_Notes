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

