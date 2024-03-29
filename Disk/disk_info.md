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

In /sys/class/ata_port/ata${n}/device/, you can see a host${x} folder. E.g., on my machine:
```
gibby ~ # ls /sys/class/ata_port/ata1/device/
ata_port  host0  link1  power  uevent
gibby ~ # ls /sys/class/ata_port/ata2/device/
ata_port  host1  link2  power  uevent
gibby ~ # lsscsi
[0:0:0:0]    disk    ATA      WDC WD1002FAEX-0 1D05  /dev/sda
[1:0:0:0]    disk    ATA      WDC WD2001FFSX-6 0A81  /dev/sdb
[2:0:0:0]    disk    ATA      WDC WD1002FAEX-0 1D05  /dev/sdc
[3:0:0:0]    disk    ATA      WDC WD2001FFSX-6 0A81  /dev/sdd
[5:0:0:0]    disk    ATA      SAMSUNG MZ7TD256 2L5Q  /dev/sde
```
The ${x} in host${x} refers to that first number in the [0:0:0:0]. So for me ata1 refers to host0 which can also be represented in SCSI form as 0:*:
```
gibby ~ # lsscsi 0:\*
[0:0:0:0]    disk    ATA      WDC WD1002FAEX-0 1D05  /dev/sda
```
Other cases:
```
ata6.00: exception Emask 0x10 SAct 0x8 SErr 0x280100 action 0x6 frozen
ata6.00: irq_stat 0x08000000, interface fatal error
ata6: SError: { UnrecovData 10B8B BadCRC }
ata6.00: failed command: READ FPDMA QUEUED
ata6.00: cmd 60/00:18:00:44:0a/04:00:fd:01:00/40 tag 3 ncq 524288 in
         res 40/00:18:00:44:0a/00:00:fd:01:00/40 Emask 0x10 (ATA bus error)
ata6.00: status: { DRDY }
ata6: hard resetting link
ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
ata6.00: configured for UDMA/133
ata6: EH complete
----------------------
[4:0:0:0]    disk    ATA      ST4000NM0033-9ZM SN04  /dev/sda 
[5:0:0:0]    disk    ATA      ST8000NM0055-1RM SN02  /dev/sdb 
[6:0:0:0]    disk    ATA      ST8000NM0055-1RM SN02  /dev/sdc 
```
So we know it is /dev/sdc device

Other case:
```
# Find ata6. Credit 'Nguyễn Anh Dũng - TK'
```
ata=6; ls -l /sys/block/sd* | grep $(grep $ata /sys/class/scsi_host/host*/unique_id | awk -F'/' '{print $5}')
```

### View disk raid info
```
mdadm -D /dev/md126
```

### Mount disk not working after replace new disk
- Old disk is fucked ( sdb ) and replaced by new disk ( sdc ), after format and mount but it isn't working, instead of reboot we can run `systemctl daemon-reload` then doing mount again, it will works!

