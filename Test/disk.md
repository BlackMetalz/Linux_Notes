## Test disk write / read speed in Linux
- Recommend test on fresh boot instead of loading

- Testing write speed on SSD Samsung Evo 850 250Gb:
```
root@EliteBook:/ssd250Gb# dd if=/dev/zero of=/root/test.tmp bs=1M count=2048
2048+0 records in
2048+0 records out
2147483648 bytes (2.1 GB, 2.0 GiB) copied, 1.41237 s, 1.5 GB/s
```

- Testing write speed on SSD Sandisk i forgot the model 250Gb:
```
root@EliteBook:/ssd250Gb# dd if=/dev/zero of=/ssd250Gb/test.tmp bs=1M count=2048
2048+0 records in
2048+0 records out
2147483648 bytes (2.1 GB, 2.0 GiB) copied, 1.31303 s, 1.6 GB/s
```

- Testing read speed on SSD Samsung Evo 850 250Gb:
```
root@EliteBook:/ssd250Gb# time dd if=/root/test.tmp of=/dev/null bs=1M
2048+0 records in
2048+0 records out
2147483648 bytes (2.1 GB, 2.0 GiB) copied, 0.285889 s, 7.5 GB/s

real	0m0.289s
user	0m0.000s
sys	0m0.289s
```

- Testing read speed on SSD Sandisk i forgot the model 250Gb:
```
root@EliteBook:/ssd250Gb# time dd if=/root/test.tmp of=/dev/null bs=1M
2048+0 records in
2048+0 records out
2147483648 bytes (2.1 GB, 2.0 GiB) copied, 0.285889 s, 7.5 GB/s

real	0m0.289s
user	0m0.000s
sys	0m0.289s
```

SSD Samsung seem like slow abit probably i use Samsung for OS. And sandisk is just extended disk and no disk usage while doing test.
