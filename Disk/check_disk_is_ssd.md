- Method 1: 
```
cat /sys/block/sdb/queue/rotational
```

```
This is an excellent way to check if you’re only interested in a single volume. Once again, a value of 0 indicates the presence of SSD technology while a value of 1 indicates a rotational drive. Both of these commands are extremely easy to use, require no real playing around and don’t require you to have any sort of administrative privileges to run. They’re just the thing if you’re constantly adding and removing volumes from a particular installation.

```

if it return 0. It is SSD
if it return 1. It is HDD

- Method 2: 
```
lsblk -o name,rota
```

```
NAME    ROTA
sda        0
└─sda1     0
sdb        1
├─sdb1     1
├─sdb2     1
├─sdb3     1
├─sdb4     1
├─sdb5     1
├─sdb6     1
├─sdb7     1
├─sdb8     1
├─sdb9     1
└─sdb10    1
```

As i mentioned above: ROTA = 0 is SSD. ROTA = 1 is HDD
```
It’s also possibly another kind of rotational device. For example if the device name sr0 came up, then that was actually more than likely an attached optical drive. Partitions cut on rotational drives will also show up as rotational. So if you had a device called sda that featured the number 1 followed by sda2 and sda1 also having a value of 1, then you can be sure these are all on the same rotational disk. Any volume followed by a number 0 will instead be on a solid-state drive. This makes sense, since solid-state drives don’t spin, and therefore they’re never classed as rotational.
```



Credit: https://appuals.com/know-youre-using-ssd-hdd-parts-linux/
