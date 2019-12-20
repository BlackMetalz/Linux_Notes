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
