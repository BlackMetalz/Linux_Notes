- Example: 

```
/data/abc/xyz/logs/vote.log {
        su user1 user   # run as specific user
        daily
        missingok
        rotate 3
        compress
        notifempty
        nodateext
}
```

rotate 3: keep 3 days of logs


More detail: https://www.digitalocean.com/community/tutorials/how-to-manage-logfiles-with-logrotate-on-ubuntu-16-04


- Atop logrotate example:

```

/var/log/atop/atop_[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9] {
        daily
        missingok
        rotate 3
        compress
        notifempty
        nodateext
        postrotate
                find /var/log/atop/ -mtime +3 -delete
                find /var/log/atop/ -empty -delete
                systemctl restart atop > /dev/null 2>&1
        endscript
}
```
