- See total threads: 
```
ps -eo nlwp | tail -n +2 | awk '{ num_threads += $1 } END { print num_threads }'
```

- Count how many thread opened by process ID:
```
ps -ef -T | grep 3529357 | wc -l
```

- Search process : This can be process name or username
```
ps -ef | grep keytoserach
```
