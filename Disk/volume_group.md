- Fdisk + DF before
```
Disk /dev/sda: 50 GiB, 53687091200 bytes, 104857600 sectors
Disk model: Virtual disk    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0ED0A2D6-0F98-4ADE-BBC0-35A66DD88B97

Device       Start       End   Sectors Size Type
/dev/sda1     2048      4095      2048   1M BIOS boot
/dev/sda2     4096   4198399   4194304   2G Linux filesystem
/dev/sda3  4198400 104855551 100657152  48G Linux filesystem

Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 24 GiB, 25769803776 bytes, 50331648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

/dev/mapper/ubuntu--vg-ubuntu--lv   24G   19G  3.3G  86% /

```


- `vgdisplay`
```
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <48.00 GiB
  PE Size               4.00 MiB
  Total PE              12287
  Alloc PE / Size       6143 / <24.00 GiB
  Free  PE / Size       6144 / 24.00 GiB
  VG UUID               IN2pDE-iGDX-tcs6-hy5f-0WhH-lXyF-EfRsdT
```

- `lvdisplay`
```
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/ubuntu-lv
  LV Name                ubuntu-lv
  VG Name                ubuntu-vg
  LV UUID                ZLQp9a-wS4V-pqDd-PFiR-O34J-95Pb-yXI9qe
  LV Write Access        read/write
  LV Creation host, time ubuntu-server, 2023-09-12 17:15:17 +0700
  LV Status              available
  # open                 1
  LV Size                <24.00 GiB
  Current LE             6143
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
```

- extend:
```
lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
  Size of logical volume ubuntu-vg/ubuntu-lv changed from 24.00 GiB (6144 extents) to <48.00 GiB (12287 extents).
  Logical volume ubuntu-vg/ubuntu-lv successfully resized.
```

- Finish by resize:
```
resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

- Fdisk + DF after:
```
Disk /dev/sda: 50 GiB, 53687091200 bytes, 104857600 sectors
Disk model: Virtual disk    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0ED0A2D6-0F98-4ADE-BBC0-35A66DD88B97

Device       Start       End   Sectors Size Type
/dev/sda1     2048      4095      2048   1M BIOS boot
/dev/sda2     4096   4198399   4194304   2G Linux filesystem
/dev/sda3  4198400 104855551 100657152  48G Linux filesystem

Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 48 GiB, 51535413248 bytes, 100655104 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


/dev/mapper/ubuntu--vg-ubuntu--lv   48G   19G   26G  43% /
```
