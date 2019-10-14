- Example related to Disk fucked and need to replace asap
```
/var/log/syslog.1:Oct 13 19:39:29 asdasd smartd[1480]: Device: /dev/sdb [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 72 to 73
/var/log/syslog.1:Oct 13 20:09:34 asdasd smartd[1480]: Device: /dev/sdb [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 73 to 74
/var/log/syslog.1:Oct 13 21:09:34 asdasd smartd[1480]: Device: /dev/sdb [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 74 to 75
/var/log/syslog.1:Oct 13 22:09:34 asdasd smartd[1480]: Device: /dev/sdb [SAT], SMART Prefailure Attribute: 1 Raw_Read_Error_Rate changed from 75 to 76
/var/log/syslog.1:Oct 13 22:46:49 asdasd sh[1490]: sh: echo: I/O error
/var/log/syslog.1:Oct 13 22:46:49 asdasd kernel: [    1.812105] ERST: Error Record Serialization Table (ERST) support is initialized.
/var/log/syslog.1:Oct 13 22:46:49 asdasd kernel: [    3.656382] RAS: Correctable Errors collector initialized.
/var/log/syslog.1:Oct 13 22:46:49 asdasd kernel: [   11.381800] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/syslog.1:Oct 13 22:46:49 asdasd kernel: [   13.185681] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
```
