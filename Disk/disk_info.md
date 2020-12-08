- Get disk serial or model or full disk parameters
```
hdparm -I /dev/sdx | grep Model # Get the fucking Model Number
hdparm -I /dev/sdx | grep Serial # get the fucking serial number
```
- Incase disk is raid, use this instead of haparm

```
smartctl -i /dev/sdx | grep 'Serial'
```

- Incase of disk RO:

```
lsblk --nodeps -o name,serial
```

- Or even better info

```
[root@SVR497L ~]# udevadm info --query=all --name=/dev/sda | grep -i serial
E: ID_SERIAL=ST4000NM0033-9ZM170_Z1ZBJ9P7
E: ID_SERIAL_SHORT=Z1ZBJ9P7
```

- True serial?:
```
smartctl -a -d sat /dev/sg17  | grep serial
```



### In case of error like show error in ata5 and you don't know what is ata5
Source: https://serverfault.com/questions/244944/linux-ata-errors-translating-to-a-device-name

dmesg -T
```
[Sun Dec  6 01:32:31 2020] ata5.00: exception Emask 0x10 SAct 0x1000 SErr 0x280100 action 0x6 frozen
[Sun Dec  6 01:32:31 2020] ata5.00: irq_stat 0x08000000, interface fatal error
[Sun Dec  6 01:32:31 2020] ata5: SError: { UnrecovData 10B8B BadCRC }
[Sun Dec  6 01:32:31 2020] ata5.00: failed command: READ FPDMA QUEUED
[Sun Dec  6 01:32:31 2020] ata5.00: cmd 60/00:60:00:40:50/01:00:2a:00:00/40 tag 12 ncq 131072 in
         res 40/00:60:00:40:50/00:00:2a:00:00/40 Emask 0x10 (ATA bus error)
[Sun Dec  6 01:32:31 2020] ata5.00: status: { DRDY }
[Sun Dec  6 01:32:31 2020] ata5: hard resetting link
[Sun Dec  6 01:32:31 2020] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[Sun Dec  6 01:32:31 2020] ata5.00: supports DRM functions and may not be fully accessible
[Sun Dec  6 01:32:31 2020] ata5.00: disabling queued TRIM support
[Sun Dec  6 01:32:31 2020] ata5.00: supports DRM functions and may not be fully accessible
[Sun Dec  6 01:32:31 2020] ata5.00: disabling queued TRIM support
[Sun Dec  6 01:32:31 2020] ata5.00: configured for UDMA/133
[Sun Dec  6 01:32:31 2020] ata5: EH complete
```
```
[root@KIMOCHI ~]# lspci | grep -i sata
00:11.4 SATA controller: Intel Corporation C610/X99 series chipset sSATA Controller [AHCI mode] (rev 05)
00:1f.2 RAID bus controller: Intel Corporation C600/X79 series chipset SATA RAID Controller (rev 05)
```

```
[root@SVR785C ~]# cat /sys/devices/pci0000\:00/0000\:00\:1f.2/ata5/host4/scsi_host/host4/unique_id 
5 # This is the number we need
```

```
dmesg | grep '5:.:.:.'
[    3.563426] scsi 5:0:0:0: Direct-Access     ATA      Samsung SSD 850  2B6Q PQ: 0 ANSI: 5
[    3.579720] sd 5:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.579973] sd 5:0:0:0: [sdb] Write Protect is off
[    3.579980] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.580028] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.582817] sd 5:0:0:0: [sdb] Attached SCSI disk
[    5.501377] sd 5:0:0:0: Attached scsi generic sg1 type 0
```
