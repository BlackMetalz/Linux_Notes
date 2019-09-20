- clean up folder /usr/src or /boot in ubuntu without manually delete:
```
apt autoremove
```

- find file olders than 7 days and delete
```
find /var/log/haproxy* -mdate +7 -exec rm -f {} \;
```

if you want make sure you don't delete wrong file, change -f to -i to confirm before delete

