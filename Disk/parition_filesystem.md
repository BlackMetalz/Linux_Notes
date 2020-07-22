### Data Demo
```
[root@SVR191L data]# fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes, 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```


- mkfs is used to build a Linux file system on a device, usually a hard disk partition

`
mkfs.ext4 /dev/sdx
`

or 
`
mkfs -t ext4 /dev/sdx
`

Command above will create an ext4 file system on disk /dev/sdx

Then we have to mount it.
First add new entry in fstab

`
UUID=c150c97e-fc78-45e1-89e0-47ce70887378 /data		  	  ext4	  noatime,nodiratime 0 2
`

UUID get from blkid. Alway recommends use UUID because it is static.
Example: when we mount with /dev/sdbx instead of UUID. So when we unpluged disk for swap or something like that. mount dir can be read wrong because /dev/sdx isn't static. This is rarely happens but when i work in production server, I never seen disk mount by /dev/sdx :D. Just my working experience

`
/data ext4 noatime,nodiratime 0 2  ( Go here if you want more detail https://wiki.debian.org/fstab :v )
`

then create directory for mount : `mkdir /data` 

then do command for mount: `mount -a` ( param -a explain in man mount )

but when we check with command df -h:
it will show something like this:
```
[root@SVR191L data]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       376G  2.6G  354G   1% /
devtmpfs        7.8G     0  7.8G   0% /dev
tmpfs           7.8G   12K  7.8G   1% /dev/shm
tmpfs           7.8G  9.0M  7.8G   1% /run
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1       976M  130M  780M  15% /boot
/dev/sda3        30G  402M   28G   2% /var
/dev/sda6       9.8G   37M  9.2G   1% /tmp
/dev/sda5        30G   49M   28G   1% /var/log
/dev/sda8       4.8G   22M  4.6G   1% /var/log/audit
tmpfs           1.6G     0  1.6G   0% /run/user/1002
/dev/sdb        917G   77M  871G   1% /data
```

Ok where is my fucking data available, it isn't enough!

nahh, it reversed by linux distribution for the root
Explain here, copy from internet:
`
This one came in handy when I bought a 1TB hard drive last week. Most linux distributions reserve 5% of new partitions for the root user and system services. The idea here is even when you run out of disk space, the root user should still be able to log in and system services should still run… this won’t happen if there is no space on the root partition. This policy may have been appropriate in the 90s when hard disk capacities were relatively low but this is 2010 and one can get a 1TB hard drive for a couple of hundred Ghana Cedis. 5% of that is about 51GB and those system services need only a couple of hundred megabytes.
`

So now we know why Available data is not equal to Size data.
btw we can tunnel it by command
```
tune2fs -m 1 /dev/sdb
```
where is 1 stand for 1% data

```
[root@SVR191L data]# tune2fs -m 1 /dev/sdb
tune2fs 1.42.9 (28-Dec-2013)
Setting reserved blocks percentage to 1% (2441906 blocks)
[root@SVR191L data]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       376G  2.6G  354G   1% /
devtmpfs        7.8G     0  7.8G   0% /dev
tmpfs           7.8G   12K  7.8G   1% /dev/shm
tmpfs           7.8G  9.0M  7.8G   1% /run
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1       976M  130M  780M  15% /boot
/dev/sda3        30G  402M   28G   2% /var
/dev/sda6       9.8G   37M  9.2G   1% /tmp
/dev/sda5        30G   49M   28G   1% /var/log
/dev/sda8       4.8G   22M  4.6G   1% /var/log/audit
tmpfs           1.6G     0  1.6G   0% /run/user/1002
/dev/sdb        917G   77M  908G   1% /data
```

We can see Available data changed. But i still recommend for keep it default as 5% reserved.
That is just my note while learning and working.


## XFS (vdc): Filesystem has duplicate UUID d04fa43b-39b7-4295-99a2-40521e64c795 - can't mount
Reboot. Lulz

Or get new UUID

```
xfs_admin -U generate /dev/vdc
```


### some note about fdisk
- fdisk only support mbr and mbr only support max to 2Tb size of partition. So we want to create new partition over 2Tb, use parted

## Parted Usage
- install parted

```
parted # Open Parted
select/dev/sdx # Select disk device for partition
mklabel gpt # Create label 
mkpart primary 0 -1 # use full disk to create partition
```

Then use mkfs vv.vv
