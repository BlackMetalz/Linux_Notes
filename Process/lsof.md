- Find the PID opened the most files by user

```
lsof -u username | awk '{print $2}' | sort | uniq -c | sort -rn | head -10
```
Example Output:

```
  54548 3846917
   2128 1020895
   1356 919184
   1265 304786
   1064 3728507
    633 1969953
    524 347995
    304 3763826
    290 546367
    253 992854
```

You can see PID 3846917 opened 54548 files
You can count again by
```
ls /proc/3846917/fd/ | wc -l
```


- With watch command:

```
watch 'lsof -u apache | awk '\''{print $2}'\'' | sort | uniq -c | sort -n'
```

Credit: https://stackoverflow.com/questions/18788811/how-many-open-files-for-each-process-running-for-a-specific-user-in-linux
