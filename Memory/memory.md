- Example: 
```
Memory 11:33:15 CRIT - RAM used: 80.96 GB of 125.52 GB, Swap used: 7.58 GB of 7.63 GB (99.4%, warn/crit at 95.0%/99.0%)(!!), Total virtual memory used: 88.54 GB of 133.15 GB (66.5%),
```

in thise case we have to drop cache and shutdown swap then turn on swap. Progress of swapoff will take lots of time, open new console and do free -mh to see swap is decreasing
