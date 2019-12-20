- Example: 

```
/data/abc/xyz/logs/vote.log {
        daily
        missingok
        rotate 3
        compress
        notifempty
        nodateext
}
```

rotate 3: keep 3 days of logs
